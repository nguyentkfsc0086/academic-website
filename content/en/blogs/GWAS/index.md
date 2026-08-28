---
title: "GWAS: My Learning Notes"
date: 2026-26-08
type: post
tag: 
    - Biostatistics

authors:
  - admin

summary: "Personal notes on what I learned while working with genome-wide association studies, from genotype data processing to association testing, interpretation, and visualization."

categories:
  - Researching

tags:
  - GWAS
  - Statistical Genetics
  - Biostatistics
  - PLINK

math: true
toc: true
featured: false
---

> [!NOTE]
> This is my personal learning note, not a standard procedure for conducting a GWAS.
> The scripts here are adapted from code I used on my university's high-performance
> computing cluster (HPC), so some commands, file paths, software modules, or
> configurations may need to be modified before running on a local computer.
>
> The quality-control thresholds and modeling choices shown here are examples from
> my own work and should not be treated as universal defaults.

## What is GWAS?

A **Genome-Wide Association Study (GWAS)** is a statistical approach used to
search across a large number of genetic variants and identify variants that are
associated with a trait or disease.

One way I found useful to think about GWAS is as a very large collection of
statistical association tests. For each genetic variant, we ask whether the
genotype helps explain variation in the phenotype after accounting for other
variables that may also affect the phenotype.

For example, suppose we are interested in **gray matter volume in the brain**.
A GWAS can ask:

> Are there genetic variants associated with differences in gray matter volume
> across individuals?

For a quantitative phenotype, this question can be expressed using a regression
model such as

{{< math >}}

\[
Y_i = \beta_0 + \beta_1 X_i + \epsilon_i
\]

{{< /math >}}

where

- $Y_i$ is the phenotype of individual $i$,
- $G_i$ is the genotype for a particular variant,
- $X_{i1},\ldots,X_{ik}$ are covariates,
- $\beta_{\mathrm{SNP}}$ represents the estimated association between the
  variant and the phenotype.

The same type of model is then repeated across many variants.

An important point is that **association does not imply causation**. A
significant GWAS result tells us that a variant is statistically associated
with a phenotype; it does not, by itself, establish the biological mechanism
causing the phenotype.

## Prerequisites

Before running an association test, I found it helpful to understand a few
pieces of the data first.

### Genetic variants and genotypes

A **single-nucleotide polymorphism (SNP)** is a position in the genome where
individuals may carry different nucleotides.

For a biallelic SNP, an additive genotype is often represented by the number of
copies of one allele:

| Genotype | Dosage |
|---|---:|
| 0 copies of the effect allele | 0 |
| 1 copy of the effect allele | 1 |
| 2 copies of the effect allele | 2 |

This $0/1/2$ value can then be used as $G_i$ in a regression model.

### Phenotype

The **phenotype** is the trait or outcome that we want to study.

Examples include:

- disease status,
- gray matter volume,
- hippocampal volume,
- biomarker concentration.

In my work, many of the phenotypes were quantitative brain-imaging or clinical
traits.

### Covariates

Covariates are variables included in the model because they may also be related
to the phenotype.

Depending on the scientific question and dataset, these may include variables
such as

- age,
- sex,
- total brain volume,
- disease status,
- genetic principal components.

The appropriate covariates depend on the study design. Adding more covariates
is not automatically better; they should be motivated by the scientific
question and analysis plan.

### VCF files

A **Variant Call Format (VCF)** file stores genetic variant information and
genotypes for a set of samples.

In my project, the starting genetic data were stored as chromosome-level
compressed VCF files. I converted these files into PLINK format before the
association analysis.

### PLINK files: BED, BIM, and FAM

PLINK commonly stores binary genotype datasets using three files:

- `.bed` — binary genotype data,
- `.bim` — variant information,
- `.fam` — sample information.

For example, a row from a BIM file may look like

```text
10    rs7070067    0    122328    T    C
```

which contains information about the chromosome, variant ID, genomic position,
and alleles.

A FAM file contains sample-level information. In one of my datasets, the
phenotype field initially contained `-9`, meaning that the phenotype was
missing and needed to be supplied separately.

## Processing the Data

A large part of my experience with GWAS happened **before** the actual
regression. The genotype and phenotype data first had to be converted,
matched, checked, and prepared.

### Converting VCF files to PLINK format

A simplified version of the conversion command I used is

```bash
plink --vcf chromosome.vcf.gz \
    --double-id \
    --biallelic-only strict \
    --set-missing-var-ids "@:#_\$1_\$2" \
    --make-bed \
    --out chromosome
```

This produces the corresponding BED, BIM, and FAM files.

For a genome-wide dataset stored by chromosome, the chromosome-level PLINK
files can then be merged before further analysis.

> The exact commands needed here depend strongly on the dataset and computing
> environment. My original scripts were written for an HPC environment and
> included cluster-specific paths and software modules.

### Quality Control

Genotype data can contain missing calls, extremely rare variants, or variants
that fail other quality checks. Quality control (QC) is therefore performed
before the association analysis.

The filters below are examples that I used in one project.

#### Sample missingness

I removed samples with more than 5% missing genotype calls:

```bash
plink --bfile data \
    --mind 0.05 \
    --make-bed \
    --out data_qc1
```

Here, `--mind 0.05` removes individuals whose genotype missingness exceeds the
specified threshold.

#### Variant missingness

I then removed variants with more than 5% missing genotype calls:

```bash
plink --bfile data_qc1 \
    --geno 0.05 \
    --make-bed \
    --out data_qc2
```

#### Minor allele frequency

Very rare variants may be difficult to analyze reliably in a dataset with a
limited sample size. In this analysis, I used

```bash
plink --bfile data_qc2 \
    --maf 0.01 \
    --make-bed \
    --out data_qc3
```

to retain variants with minor allele frequency (MAF) of at least 1%.

#### Hardy-Weinberg equilibrium

I also used a Hardy-Weinberg equilibrium filter:

```bash
plink --bfile data_qc3 \
    --hwe 1e-6 \
    --make-bed \
    --out data_qc_final
```

A strong departure from Hardy-Weinberg equilibrium can sometimes be a sign of
genotyping problems or other features of the data that deserve attention.

Again, these thresholds are **examples from my analysis**, not a universal GWAS
recipe.

### Linkage Disequilibrium Pruning

Nearby genetic variants can be highly correlated because of **linkage
disequilibrium (LD)**.

For principal component analysis, I wanted a less redundant set of variants, so
I performed LD pruning:

```bash
plink --bfile data_qc_final \
    --indep-pairwise 50 5 0.2 \
    --out pca_pruning
```

The resulting `pca_pruning.prune.in` file contains the variants retained for
the PCA.

An intuitive way I think about this step is
{{< math >}}

\[
\text{many correlated variants}
\longrightarrow
\text{less redundant variant set}
\longrightarrow
\text{PCA}.
\]

{{< /math >}}


### Principal Component Analysis

Genetic ancestry and population structure can create confounding in an
association analysis.

Individuals with different genetic ancestry may have different allele
frequencies. If ancestry is also related to the phenotype, we may observe an
apparent SNP--phenotype association that is partly explained by population
structure.

To summarize major directions of genetic variation, I calculated genetic
principal components using the LD-pruned variants:

```bash
plink --bfile data_qc_final \
    --extract pca_pruning.prune.in \
    --pca 10 \
    --out pca_results
```

This generated ten principal components,

$$
PC_1, PC_2, \ldots, PC_{10},
$$

which could then be included as covariates in the association model.

## Association Testing

For a quantitative phenotype, I used linear regression to test whether the
genotype of a variant was associated with the phenotype.

A simplified model is

$$
Y_i =
\beta_0
+
\beta_{\mathrm{SNP}}G_i
+
\beta_1\mathrm{Age}_i
+
\beta_2\mathrm{Sex}_i
+
\sum_{j=1}^{10}\gamma_j PC_{ji}
+
\epsilon_i.
$$

The hypothesis test for the SNP effect is

$$
H_0:\beta_{\mathrm{SNP}}=0
$$

versus

$$
H_A:\beta_{\mathrm{SNP}}\neq0.
$$

The null hypothesis says that, conditional on the covariates in the model, the
variant is not associated with the phenotype.

A simplified PLINK command looks like

```bash
plink --bfile data_qc_final \
    --linear \
    --pheno phenotype.txt \
    --covar covariates.txt \
    --covar-name SEX,AGE,PC1,PC2,PC3,PC4,PC5,PC6,PC7,PC8,PC9,PC10 \
    --hide-covar \
    --out gwas_results
```

### A more complicated model I encountered in research

While trying to reproduce a previous analysis of brain imaging phenotypes, I
encountered a model with additional covariates and interaction terms.

For gray matter volume, the model had the form

$$
\begin{aligned}
\mathrm{GrayMatterVolume}_i
={}&
\beta_0
+
\beta_{\mathrm{SNP}}G_i
+
\beta_1\mathrm{Age}_i
+
\beta_2\mathrm{Age}_i^2 \\
&+
\beta_3\mathrm{Sex}_i
+
\beta_4(\mathrm{Age}_i\times\mathrm{Sex}_i)
+
\beta_5(\mathrm{Age}_i^2\times\mathrm{Sex}_i) \\
&+
\beta_6\mathrm{TBV}_i
+
\sum_{j=1}^{10}\gamma_j PC_{ji}
+
\beta_{\mathrm{status}}\mathrm{Status}_i
+
\epsilon_i.
\end{aligned}
$$

Here, TBV represents total brain volume and the genetic principal components
were included to account for population structure.

I include this example because it helped me see that the basic GWAS idea is
simple, while the actual model used in a study can depend heavily on the
scientific question and dataset.

<!-- TODO: Add citation to the paper/model being reproduced. -->

## Interpreting the Results

A PLINK association result may look something like

```text
CHR  SNP              BP        A1  TEST  NMISS  BETA      STAT     P
1    1:10177_A_AC     10177     A   ADD   2504   0.0123    0.456    0.6483
1    rs367896724      10235     A   ADD   2504  -0.0089   -0.321    0.7482
11   11:89920705_C_T  89920705  C   ADD   1814  -0.2079   -5.643    1.941e-08
```

Several columns are particularly important when I interpret the result.

### Effect allele

`A1` is the allele relative to which the additive effect is reported in this
output.

The interpretation of the sign of beta therefore depends on knowing which
allele is being treated as the effect allele.

### Beta

`BETA` is the estimated regression coefficient for the genotype.

For example, if

$$
\widehat{\beta}_{\mathrm{SNP}}=-0.2079,
$$

then each additional copy of the effect allele is associated with an estimated
decrease of 0.2079 units in the phenotype, **conditional on the covariates in
the model**.

The units of beta depend on the units of the phenotype.

### P-value

The p-value is calculated for the hypothesis

$$
H_0:\beta_{\mathrm{SNP}}=0.
$$

A small p-value indicates that the observed association would be difficult to
reconcile with the null hypothesis under the assumptions of the model.

It does **not** tell us

- the probability that the null hypothesis is true,
- the probability that the SNP causes the phenotype,
- whether the effect is biologically important.

### Genome-wide significance

Because a GWAS may test hundreds of thousands or millions of variants, using a
threshold such as $p<0.05$ would generate many false-positive findings simply
because of the number of tests.

A commonly used genome-wide significance threshold is

$$
p < 5\times10^{-8}.
$$

In one of my scripts, I extracted variants passing this threshold using

```bash
awk 'NR==1 || ($9 != "NA" && $9 < 5e-8)' \
    gwas_results.assoc.linear > significant_snps.txt
```

The exact statistical considerations behind genome-wide significance are more
subtle than a single cutoff, but this threshold is a useful reference point
when first learning to read GWAS results.

### Effect Direction and Replication

One question I encountered in my research was how to compare GWAS results from
different datasets.

Suppose a previous study reports

$$
\widehat{\beta}_{\mathrm{previous}}>0.
$$

If I test the same variant in another dataset and obtain

$$
\widehat{\beta}_{\mathrm{new}}>0,
$$

then the estimated effects have the **same direction**.

If instead

$$
\widehat{\beta}_{\mathrm{new}}<0,
$$

the directions are opposite.

Importantly, a variant can have a consistent direction of effect across two
datasets without reaching genome-wide significance in both datasets.
Statistical significance also depends on factors such as sample size,
variability, allele frequency, model specification, and effect size.

This was particularly useful for me when comparing association results from
ADNI with variants reported in previous studies.

<!-- TODO: Add a small, non-sensitive example table comparing effect directions. -->

## Visualization

### Manhattan Plot

A Manhattan plot provides a compact visualization of GWAS p-values across the
genome.

For each tested variant, the y-coordinate is

$$
-\log_{10}(p).
$$

For example,

$$
-\log_{10}(5\times10^{-8})\approx 7.30.
$$

This transformation means that **smaller p-values appear higher on the plot**.

The plot can be read as follows:

- **x-axis:** genomic position, arranged by chromosome,
- **y-axis:** $-\log_{10}(p)$,
- **each point:** one tested genetic variant,
- **horizontal significance line:** a chosen genome-wide significance
  threshold,
- **peaks:** genomic regions containing variants with comparatively strong
  statistical evidence of association.

A simplified Python version of the plotting code I used is

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

df = pd.read_csv("gwas_results.assoc.linear", sep=r"\s+")

## Keep the additive test and valid p-values
df = df[df["TEST"] == "ADD"].copy()
df["CHR"] = pd.to_numeric(df["CHR"], errors="coerce")
df["BP"] = pd.to_numeric(df["BP"], errors="coerce")
df["P"] = pd.to_numeric(df["P"], errors="coerce")
df = df.dropna(subset=["CHR", "BP", "P"])
df = df[(df["P"] > 0) & (df["P"] <= 1)]

df["minus_log10_p"] = -np.log10(df["P"])
df = df.sort_values(["CHR", "BP"])

## Construct cumulative genomic positions
current_pos = 0
ticks = []
labels = []

for chrom in sorted(df["CHR"].unique()):
    idx = df["CHR"] == chrom
    df.loc[idx, "BP_cum"] = df.loc[idx, "BP"] + current_pos

    ticks.append(df.loc[idx, "BP_cum"].median())
    labels.append(str(int(chrom)))
    current_pos = df.loc[idx, "BP_cum"].max()

plt.figure(figsize=(14, 6))

for chrom in sorted(df["CHR"].unique()):
    chr_df = df[df["CHR"] == chrom]
    plt.scatter(
        chr_df["BP_cum"],
        chr_df["minus_log10_p"],
        s=8,
        alpha=0.7
    )

plt.axhline(-np.log10(5e-8), linestyle="--", linewidth=1)
plt.xticks(ticks, labels)
plt.xlabel("Chromosome")
plt.ylabel("-log10(P)")
plt.title("Manhattan Plot")
plt.tight_layout()
plt.show()
```

<!-- TODO: Replace this comment with a Manhattan plot from the final analysis. -->

## What I Learned

These are some of the main ideas that became clearer to me while working
through a GWAS analysis.

### 1. The statistical idea behind GWAS is relatively simple

For a quantitative trait, I can think of GWAS as repeatedly fitting a
regression model in which the SNP genotype is one of the predictors.

The scale of the analysis is what makes GWAS challenging: this test may be
repeated for millions of variants.

### 2. Much of the work happens before the regression

Before I could interpret a single p-value, I had to deal with tasks such as

- converting genotype files,
- matching sample IDs,
- preparing phenotypes,
- preparing covariates,
- performing QC,
- LD pruning,
- PCA.

This made me realize that data preparation is a major part of a genetic
association analysis.

### 3. Population structure matters

Genetic differences between groups of individuals can create confounding if
population structure is associated with both allele frequencies and the
phenotype.

Using genetic principal components as covariates helped me understand how PCA
connects a familiar mathematical technique with a practical statistical
genetics problem.

### 4. A small p-value is not the whole story

A p-value is evidence about a statistical association under a model. It does
not directly tell me whether an effect is large, biologically important, or
causal.

When comparing results across datasets, I also found it useful to examine the
estimated effect size, effect allele, and direction rather than looking only at
whether a variant crossed a significance threshold.

### 5. Model specification matters

The covariates and interaction terms included in an analysis can change the
estimated association and the number of usable samples.

The appropriate model should therefore come from the scientific question and
study design rather than from adding every available variable.

## After GWAS: What Next?

Finding a statistically associated variant is often only the beginning.

A GWAS result does not immediately explain which gene is affected or what
biological mechanism connects the variant to the phenotype.

Two ideas that I encountered after learning the basic GWAS workflow were
**eQTL analysis** and **gene-based analysis**.

### eQTLs

An expression quantitative trait locus (eQTL) analysis asks whether genetic
variation is associated with gene-expression levels.

Conceptually, this creates a possible bridge

$$
\text{genetic variant}
\longrightarrow
\text{gene expression}
\longrightarrow
\text{biological interpretation}.
$$

In my project, one of the next questions after identifying GWAS variants was
whether those variants were also associated with the expression of particular
genes.

### Gene-based analysis

I also encountered tools such as **MAGMA**, which can aggregate
variant-level association information into gene-level analyses.

I consider both eQTL analysis and gene-based analysis separate topics from the
basic GWAS workflow, so I may write more detailed learning notes about them in
the future.

## References

- GWAS tutorial used while learning: <https://cloufield.github.io/GWASTutorial/>
- PLINK: <https://www.cog-genomics.org/plink/>
- A practical tutorial on conducting genome-wide association studies:
  <https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1004219>

<!-- TODO: Add the brain-imaging GWAS paper used for the replication example. -->
