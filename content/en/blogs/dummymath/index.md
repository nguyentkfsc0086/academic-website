---
title: Random math
date: 2025-12-09
type: post
tags:
    - Mathematics
    - Problem solving
---
### Random 1

The unit step function $(\sigma)$ is defined as

{{< math >}}
\[
\sigma(x)=
\begin{cases}
1, & x \ge 0,\\
0, & x < 0.
\end{cases}
\]
{{< /math >}}

Let

{{< math >}}
\[
f(x)=
\begin{cases}
2, & x \ge -1,\\
-3, & x < -1.
\end{cases}
\]
{{< /math >}}

Express $(f)$ as a linear transformation of the unit step function $(\sigma)$.


`Solution`

A translation of $(\sigma(x))$ by $(\xi)$ is

{{< math >}}
\[
\sigma(x-\xi)=
\begin{cases}
1, & x \ge \xi,\\
0, & x < \xi.
\end{cases}
\]
{{< /math >}}

The function $(f(x))$ jumps at $(x=-1)$, so take $(\xi=-1)$. Then

{{< math >}}
\[
f(x)=a\,\sigma(x+1)+b.
\]
{{< /math >}}

For $(x<-1)$, $(\sigma(x+1)=0)$, so $(f(x)=b=-3)$.

For $(x\ge -1\)$, $(\sigma(x+1)=1)$, so $(f(x)=a+b=2)$.

Thus,

{{< math >}}
\[
b=-3,\qquad a+b=2 \implies a=5.
\]
{{< /math >}}

Therefore,

{{< math >}}
\[
\boxed{f(x)=5\sigma(x+1)-3.}
\]
{{< /math >}}
### Random 2
---
title: "Principal Component Analysis"
date: 2026-03-31
draft: false
math: true
---

## Principle Component Analysis

> In this document, **traits = features**.  
> **iid** means **independent and identically distributed**.

### Idea

Reduce the number of features while keeping the most important information.

We originally have about **1750 traits**. After removing features with more than one null value, we are left with about **600 traits**. However, this deletion-based approach is somewhat random, so we need a more statistical way to keep the most important features.

A reasonable strategy is to:
1. Work with the non-null features first (about 600 traits).
2. Then extend the analysis to the remaining traits.

## Implementation

### Standardize the data

Standardize each feature so that it has mean 0 and standard deviation 1:

$$
Z = \frac{X - \mu}{\sigma}
$$

where:
- $Z$ is the standardized feature,
- $X$ is the original feature,
- $\mu$ is the mean,
- $\sigma$ is the standard deviation.

### Calculate the covariance matrix

The covariance matrix is:

$$
A =
\begin{pmatrix}
\operatorname{Var}(X_1) & \operatorname{Cov}(X_1,X_2) & \cdots & \operatorname{Cov}(X_1,X_n) \\
\operatorname{Cov}(X_2,X_1) & \operatorname{Var}(X_2) & \cdots & \operatorname{Cov}(X_2,X_n) \\
\vdots & \vdots & \ddots & \vdots \\
\operatorname{Cov}(X_n,X_1) & \operatorname{Cov}(X_n,X_2) & \cdots & \operatorname{Var}(X_n)
\end{pmatrix}
$$

Here, **Cov** means covariance.

For two variables $X$ and $Y$, the covariance is:

$$
\operatorname{Cov}(X,Y) = \frac{\sum_{i=1}^{n}(X_i - \bar X)(Y_i - \bar Y)}{n-1}
$$

## Find the principal components

- **PC1**: direction of maximum variance
- **PC2**: next best direction, perpendicular to PC1
- **PC3**: third best direction, perpendicular to PC2
- $\dots$
- **PC(n)**: perpendicular to PC(n-1)

### How do we find these directions?

We use the covariance matrix.

Let:
- $A$ be the covariance matrix,
- $X$ be a standardized feature vector.

For each $X$, there exists a scalar $\lambda$ such that

$$
A \cdot X = \lambda \cdot X
$$

The values $\lambda$ are the eigenvalues, and they determine the importance of each principal component.

We label the principal components in decreasing order of $\lambda$:
- the largest $\lambda$ corresponds to **PC1**,
- the second largest $\lambda$ corresponds to **PC2**,
- and so on.