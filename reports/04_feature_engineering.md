# ⚙️ Feature Engineering

# 📖 Overview

Feature Engineering is one of the most important stages in the Data Science lifecycle. The quality of features used for training often has a greater impact on model performance than the choice of machine learning algorithm itself.

Real-world datasets usually contain:

- Categorical variables
- Imbalanced classes
- Irrelevant features
- Different data representations

Machine Learning algorithms cannot directly understand raw data. Therefore, the dataset must be transformed into a suitable numerical format before model training.

The purpose of this phase is to convert the cleaned dataset into a machine-learning-ready dataset while preserving meaningful information.

---

# 🎯 Objectives

The objectives of this phase are:

✅ Convert categorical variables into numerical representations.

✅ Handle class imbalance.

✅ Prepare the dataset for machine learning algorithms.

✅ Create training and testing datasets.

✅ Improve model performance and reduce bias.

---

# 🧠 Why Feature Engineering is Important

Feature Engineering helps to:

- Improve prediction accuracy.
- Reduce noise in the data.
- Make patterns easier for algorithms to learn.
- Prevent model bias.
- Increase model interpretability.
- Produce more robust and generalizable models.

In many real-world Data Science projects, feature engineering contributes significantly to model success.

---

# 📂 Dataset Used

Input Dataset:

```text
cleaned_telco_churn.csv
```

Output Dataset:

```text
final_dataset.csv
```

---

# Step 1 – Import Required Libraries

```python
import pandas as pd
import numpy as np

from sklearn.preprocessing import LabelEncoder
from sklearn.model_selection import train_test_split
```

---

## Why are these libraries used?

### Pandas

Used for:

- Loading datasets
- Manipulating data
- Creating new features
- Saving processed data

---

### NumPy

Used for:

- Numerical operations
- Efficient array computations

---

### LabelEncoder

Used to convert categorical labels into numerical values.

Machine Learning algorithms only work with numbers.

---

### train_test_split

Used to divide the dataset into:

- Training data
- Testing data

This helps evaluate model performance on unseen data.

---

# Step 2 – Load the Cleaned Dataset

```python
df = pd.read_csv(
    "../data/processed/cleaned_telco_churn.csv"
)
```

---

## Why?

The cleaned dataset from the previous phase is used as the starting point.

This ensures that:

✅ Missing values are handled.

✅ Incorrect data types are corrected.

✅ Unnecessary features are removed.

---

# Step 3 – Identify Categorical Variables

```python
cat_cols = df.select_dtypes(
    include="object"
).columns
```

---

## Why?

Most Machine Learning algorithms cannot understand text values such as:

```text
Yes
No

Male
Female

Month-to-month
```

These variables must be converted into numbers.

---

# Step 4 – Convert Target Variable

```python
df["Churn"] = df["Churn"].map({
    "Yes":1,
    "No":0
})
```

---

## Why?

The target variable is:

```text
Yes
No
```

Machine Learning algorithms require numerical labels.

Therefore:

```text
Yes → 1
No  → 0
```

This is called **Binary Encoding**.

---

# Step 5 – Inspect Categories

```python
for col in cat_cols:
    print(col)
    print(df[col].unique())
```

---

## Why?

This helps identify:

- Binary variables
- Multi-category variables

Different encoding techniques are needed for each.

---

# Step 6 – Label Encoding

```python
binary_cols = []

for col in cat_cols:

    if df[col].nunique() == 2:

        binary_cols.append(col)
```

---

```python
le = LabelEncoder()

for col in binary_cols:

    df[col] = le.fit_transform(
        df[col]
    )
```

---

# Why Label Encoding?

Binary variables contain only two values.

Examples:

```text
Male / Female
Yes / No
```

These can be safely converted into:

```text
0 / 1
```

Example:

```text
Male   → 1
Female → 0
```

This preserves information while making the data understandable to Machine Learning models.

---

# Step 7 – One Hot Encoding

```python
multi_cols = []

for col in cat_cols:

    if df[col].nunique() > 2:

        multi_cols.append(col)
```

---

```python
df = pd.get_dummies(
    df,
    columns=multi_cols,
    drop_first=True
)
```

---

# Why One Hot Encoding?

Some variables have multiple categories.

Example:

```text
Contract

Month-to-month
One year
Two year
```

Assigning numbers:

```text
Month-to-month → 0
One year → 1
Two year → 2
```

would incorrectly imply:

```text
2 > 1 > 0
```

which has no real meaning.

Instead, One Hot Encoding creates:

```text
Contract_OneYear
Contract_TwoYear
```

This avoids introducing false relationships.

---

# Why use drop_first=True ?

This prevents:

# Dummy Variable Trap

Without dropping one column:

```text
Month-to-month
One year
Two year
```

becomes:

```text
0 0
1 0
0 1
```

The dropped category becomes the reference category.

This reduces:

- Redundant information
- Multicollinearity

which improves model stability.

---

# Step 8 – Verify Final Dataset

```python
df.shape

df.head()
```

---

## Why?

To ensure:

✅ Encoding worked correctly.

✅ All columns are numerical.

✅ Dataset is ready for Machine Learning.

---

# Step 9 – Check Class Imbalance

```python
df["Churn"].value_counts()
```

---

## Why?

Customer churn datasets are usually imbalanced.

Example:

```text
No  → 73%

Yes → 27%
```

This creates bias.

The model may simply predict:

```text
No
```

for every customer and still achieve high accuracy.

This is misleading.

---

# Step 10 – Split Data

```python
X = df.drop(
    "Churn",
    axis=1
)

y = df["Churn"]
```

---

```python
X_train,
X_test,
y_train,
y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42,
    stratify=y
)
```

---

# Why Train-Test Split?

Machine Learning models should be evaluated on unseen data.

Training and testing on the same data causes:

# Overfitting

The model memorizes instead of learning.

---

## Why use:

```python
test_size = 0.2
```

80%

Training

20%

Testing

This is an industry-standard split.

---

## Why use:

```python
random_state = 42
```

To ensure reproducibility.

Every time the notebook runs:

the same split is produced.

---

## Why use:

```python
stratify = y
```

To preserve the class distribution.

Without stratification:

the testing data may contain very few churn cases.

---

# Step 11 – Handle Class Imbalance using SMOTE

```python
from imblearn.over_sampling import SMOTE
```

---

```python
smote = SMOTE(
    random_state=42
)

X_train_smote,
y_train_smote = smote.fit_resample(
    X_train,
    y_train
)
```

---

# Why SMOTE?

SMOTE stands for:

# Synthetic Minority Over-sampling Technique

Instead of duplicating existing churn customers,

SMOTE creates:

# Synthetic Customers

by generating new samples between existing minority observations.

---

## Why is this important?

Without balancing:

Models become biased towards:

```text
No Churn
```

Balancing improves:

✅ Recall

✅ F1 Score

✅ ROC-AUC

---

# Step 12 – Verify Balance

```python
y_train_smote.value_counts()
```

Expected:

```text
0 → 4133

1 → 4133
```

Balanced dataset.

---

# Step 13 – Save Final Dataset

```python
processed_df = pd.concat(
    [
        X_train_smote,
        y_train_smote
    ],
    axis=1
)
```

---

```python
processed_df.to_csv(
    "../data/processed/final_dataset.csv",
    index=False
)
```

---

# Why save the processed dataset?

Benefits:

✅ Reproducibility

✅ Faster experimentation

✅ Avoid repeating preprocessing

✅ Better project organization

---

# Files Generated

```text
final_dataset.csv

X_test.csv

y_test.csv
```

These files will be used later for:

- Machine Learning Models
- Explainable AI
- Streamlit Application

---

# 📊 Outcome of Feature Engineering

At the end of this phase:

✅ Categorical variables were encoded.

✅ Target labels were transformed.

✅ Data imbalance was handled.

✅ Dataset was split into training and testing datasets.

✅ Final machine-learning-ready dataset was created.

---

# 💡 Business Importance

Feature Engineering allows the model to better understand customer behavior patterns.

This improves:

- Prediction accuracy
- Customer retention decisions
- Trust in the final system

A well-engineered feature set can significantly improve business decision-making.

---

# 💻 Git Commit

```bash
git add .

git commit -m "Complete feature engineering and SMOTE"
```

---

# 🚀 Next Phase

The next phase of the project is:

# Machine Learning Model Development

Models to be explored:

- Logistic Regression
- Decision Tree
- Random Forest
- XGBoost
- Support Vector Machine
- K-Nearest Neighbors

These models will be compared using:

- Accuracy
- Precision
- Recall
- F1 Score
- ROC-AUC Score
- Confusion Matrix

The best-performing model will then be selected for deployment and Explainable AI analysis.