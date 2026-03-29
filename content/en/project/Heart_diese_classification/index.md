---
title: "Heart Disease Classification"
date: 2026-01-12
type: post
tags:
  - Python
  - Machine Learning
  - Biostatistics
  - Bioinformatics
summary: "A logistic regression baseline for heart disease classification using a Kaggle dataset, with plans for external evaluation on a Hugging Face dataset."
---

## Overview

In this project, I built a baseline **logistic regression** model to classify heart disease status from clinical variables. The main goal was to train the model on a Kaggle dataset and then prepare for evaluation on a second dataset from Hugging Face.

At this stage, the model has been trained and evaluated on a train/test split from the Kaggle data. External validation on the Hugging Face dataset is the next step.

## Libraries

```python
import os
import glob
import kagglehub
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score, confusion_matrix
```

## Data sources

I used two sources:

- **Training source:** Kaggle heart disease dataset
- **Planned external evaluation source:** Hugging Face heart disease dataset

```python
# Kaggle dataset
dataset_dir = kagglehub.dataset_download("neurocipher/heartdisease")
csv_files = glob.glob(os.path.join(dataset_dir, "**", "*.csv"), recursive=True)
df_kaggle = pd.read_csv(csv_files[0])

# Hugging Face dataset
df_hugging_face = pd.read_csv("hf://datasets/buio/heart-disease/heart.csv")
```

## Kaggle dataset overview

The Kaggle dataset contains the following predictors:

- Age
- Sex
- Chest pain type
- Blood pressure
- Cholesterol
- Fasting blood sugar over 120
- EKG results
- Maximum heart rate
- Exercise-induced angina
- ST depression
- Slope of ST
- Number of vessels fluro
- Thallium

The response variable is **Heart Disease**, recorded as `Presence` or `Absence`.

### Missing values

I checked for missing values before fitting the model.

```python
df_kaggle.isna().sum()
```

The dataset did not contain any missing values, so I moved directly to model fitting.

## Hugging Face dataset overview

The Hugging Face dataset uses a slightly different naming convention for variables:

- `age`
- `sex`
- `cp`
- `trestbps`
- `chol`
- `fbs`
- `restecg`
- `thalach`
- `exang`
- `oldpeak`
- `slope`
- `ca`
- `thal`
- `target`

Before using this dataset for external testing, the feature names and category encodings need to be aligned with the Kaggle dataset.

## Logistic regression model

### Train/test split

I first trained the model on the Kaggle data using a 75/25 split.

```python
y = df_kaggle['Heart Disease']
X = df_kaggle.drop('Heart Disease', axis=1)

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.25
)
```

### Fit the model

```python
logreg = LogisticRegression(random_state=16)
logreg.fit(X_train, y_train)
y_pred = logreg.predict(X_test)
```

During training, scikit-learn returned a convergence warning. This suggests that the model may benefit from:

- increasing `max_iter`
- scaling continuous predictors
- trying a different solver

## Model performance

### Accuracy

```python
accuracy_score(y_test, y_pred)
```

The model achieved an accuracy of:

**0.8235**

### Confusion matrix

```python
cnf_matrix = confusion_matrix(y_test, y_pred)
cnf_matrix
```

Result:

```text
[[28,  7],
 [ 5, 28]]
```

This means:

- 28 true negatives
- 28 true positives
- 7 false positives
- 5 false negatives

### Plotting the confusion matrix

```python
class_names = [0, 1]
fig, ax = plt.subplots()
tick_marks = np.arange(len(class_names))
plt.xticks(tick_marks, class_names)
plt.yticks(tick_marks, class_names)

sns.heatmap(pd.DataFrame(cnf_matrix), annot=True, cmap="YlGnBu", fmt='g')
ax.xaxis.set_label_position("top")
plt.tight_layout()
plt.title('Confusion matrix', y=1.1)
plt.ylabel('Actual label')
plt.xlabel('Predicted label')
plt.show()
```

The confusion matrix suggests that the model performs reasonably well on the Kaggle test split, with a balanced number of correct predictions across both classes.

## Interpretation

This logistic regression model provides a solid baseline for heart disease classification. With an accuracy of about 82%, it captures a useful amount of signal from the clinical predictors.

That said, there are still a few limitations:

- the model showed a convergence warning
- no feature scaling was applied
- evaluation so far has only been done on the Kaggle split
- the Hugging Face dataset still needs to be standardized before external testing

## Next steps

The next stage of the project is to evaluate how well the model generalizes to data it has not seen before. To do that, I plan to:

1. align variable names between the two datasets
2. standardize categorical encodings where needed
3. fit the model with improved preprocessing
4. test performance on the Hugging Face dataset
5. compare internal and external accuracy

## Conclusion

This project shows how a simple logistic regression model can be used as a first approach to heart disease classification. Even without extensive tuning, the model performed well on the Kaggle train/test split. The most important next step is external validation, which will show whether the model can generalize beyond the training source.
