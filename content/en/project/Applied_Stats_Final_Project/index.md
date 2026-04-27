---
title: "Analysis the relationship between number of death case diagnoised with HIV/AIDS and the age of the patients"
author: "Nguyen Tran"
date: 2026-04-26
subtitle: |
  MATH 3850: Applied Statistics \
  Instructor: Prof. Guangming Jing
---
```r
library(dplyr)
library(stringr)
knitr::opts_chunk$set( #remember to change the figs/NEWNAME-, echo used to show code
  fig.path = "./figs/hw1-", results = "markup", error = FALSE, fig.width = 10,
  fig.height = 10, size = "small", echo = TRUE, tidy = FALSE, message = FALSE,
  fig.keep = "high", fig.align = "center", warning = FALSE
)
```

# Introduction:

In this project, I chose the [HIV/AIDS](https://catalog.data.gov/dataset/hiv-aids-cases?from_hint=eyJxIjoiSElWIn0%3D) dataset from the California Department of Public Health for my analysis.

# Data:

There are 4 tables in the data set that I chose:

### Deaths of persons diagnosed with hiv/aids:

```r
death_person = read.csv("data/deaths-of-persons-diagnosed-with-hiv-aids.csv", header = T)
head(death_person)
```

### hiv/aids data dictionary

```r
history = read.csv("data/hiv-aids-data-dictionary.csv", header = T)
head(history)
```

### Persons living with HIV/AIDS

```r
person_with_hiv = read.csv("data/persons-living-with-hiv-aids.csv", header = T)
head(person_with_hiv)
```

### Person diagnois with HIV/AIDS

```r
person_positive_hiv = read.csv("data/persons-newly-diagnosed-with-hiv.csv", header = T)
head(person_positive_hiv)
```

# Research question:

The research question that I want to investigate in this data set is `What is the relationship between the number of person death diagnosed with HIV/AIDS and their age?`.

To address this question, I will use `Linear regression` to analyse the relationship between the `number of death person` and their `age`. After that, I will do `Hypothesis testing` to validate if there is a correlation between the those 2 factors. This report also include the Q-Q plot to make the interpret results easier.

# Analysis

## Preprocess the data

Let recall the data that we interested:

```r
head(death_person)
```

As we can see, this data contain 4 columns:

-   Year of the record

-   Category, including:

    -   Age at Death (in years)

    -   Current Gender

    -   Race/Ethnicity

    -   Sex at Birth

    -   Transmission Category: Cisgender Men Adult or Adolescent

    -   County of Residence at Death

-   Group: the values of each category

-   Count: the number of person in each category and group

In this table, we only interested about `Age at Death (in years)`, `Group` and `Count`. So we will reorganize the table which only contain the data that we interested.

```r
# filter the columns that match the category `Age of death`
data = death_person %>%
  filter(Category == "Age at Death (in years)") %>%
  group_by(Group) %>%
  summarise(total_deaths = sum(Count, na.rm = TRUE))
head(data)
```

However, the age on the first columns are not `numerical`. So we will take the `mean` value of the group for further analysis

```r
data <- data %>%
  mutate(Age_mid = case_when(
    str_detect(Group, "to") ~ (
      as.numeric(str_extract(Group, "^\\d+")) +
      as.numeric(str_extract(Group, "\\d+$"))
    ) / 2,
    
    str_detect(Group, ">= 75") ~ 77.5,
    
    TRUE ~ NA_real_
  ))
head(data)
```

## Regression

Now we have a 'clean' data table for further analysis, we can start doing `regression`

Recall: Our regression model will have the following form:

$$
Y = \beta_0 + \beta_1X + \epsilon
$$

where $Y$ represents the number of deaths, $X$ represents the age (measured using the midpoint of each age range), and $\beta_0$​ and $\beta_1$​ are unknown parameters. The parameter $\beta_0$ is the intercept, and $\beta_1$ represents the change in the number of deaths associated with a one-unit increase in age.

Now I will run the regression model

```r
model <- lm(total_deaths ~ Age_mid, data = data)

summary(model)
```

The regression analysis shows that age is a significant predictor of the number of deaths among persons diagnosed with HIV/AIDS. The estimated slope coefficient is 67.32, indicating that for each one-year increase in age, the number of deaths increases by approximately 67 on average. The p-value for the age variable is 8.16 × 10⁻⁵, which is far below the common significance level of 0.05, leading us to reject the null hypothesis that age has no relation. Additionally, the model explains about 70.9% of the variation in deaths $r^2 = 0.709$, suggesting a strong relationship between age and mortality.

# Visualization

```r
plot(data$Age_mid, data$total_deaths,
     main = "Deaths Among Persons Diagnosed with HIV/AIDS by Age",
     xlab = "Age at Death (Midpoint)",
     ylab = "Total Deaths",
     pch = 19)

abline(model, col = "red", lwd = 2)
```

# Conclusion

This study examined the relationship between age and the number of deaths among persons diagnosed with HIV/AIDS using a linear regression model. The results show a strong and statistically significant positive association between age and deaths. Specifically, the estimated slope indicates that the number of deaths increases as age increases, and the p-value (8.16 × 10⁻⁵) provides strong evidence against the null hypothesis of no relationship. Additionally, the model explains approximately 70.9% of the variation in deaths, suggesting that age is an important factor in understanding mortality patterns in this population. Overall, the findings indicate that older age groups experience substantially higher numbers of deaths, highlighting age as a key factor associated with HIV/AIDS mortality
