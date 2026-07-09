# Data Cleaning and Preprocessing

## Overview

Data cleaning and preprocessing is one of the most important stages in the Data Science lifecycle. Real-world datasets often contain missing values, incorrect data types, duplicate records, and unnecessary features that can reduce the performance of machine learning models.

The objective of this phase is to transform the raw customer churn dataset into a clean and structured dataset that is suitable for further analysis and model development.

---

# Objectives

The objectives of this stage are to:

- Load the raw dataset.
- Identify data quality issues.
- Detect missing values.
- Correct incorrect data types.
- Remove unnecessary columns.
- Handle incomplete records.
- Save the cleaned dataset for future use.

---

# Step 1 – Import Required Libraries

The following Python libraries are imported.

- Pandas
- NumPy

These libraries provide functions for reading, cleaning, manipulating, and analyzing datasets efficiently.

---

# Step 2 – Load the Dataset

The IBM Telco Customer Churn dataset is loaded from the `data/raw` directory into a Pandas DataFrame.

This creates the working copy of the dataset while preserving the original CSV file.

---

# Step 3 – Check Missing Values

The dataset is inspected for missing values.

Initially, the dataset appears to contain no missing values.

However, missing values may sometimes be stored as blank spaces rather than actual null values.

Therefore, additional inspection is required.

---

# Step 4 – Inspect the TotalCharges Column

The `TotalCharges` column should contain numerical values representing the total amount charged to each customer.

However, it is stored as an object (string) instead of a numeric data type.

This indicates that the column contains invalid entries.

---

# Step 5 – Detect Hidden Missing Values

Blank spaces within the `TotalCharges` column are identified.

These blank spaces represent missing values that were not detected during the initial inspection.

Identifying hidden missing values is an important step in professional data preprocessing.

---

# Step 6 – Convert Data Type

The `TotalCharges` column is converted from a string (object) to a numeric data type.

Invalid values are automatically converted into `NaN`.

This allows missing values to be handled correctly.

---

# Step 7 – Handle Missing Values

After converting the column, the missing values become visible.

These missing records belong to customers with zero tenure.

Since these customers have incomplete billing information, the rows are removed from the dataset.

Removing these records improves data quality while affecting only a very small portion of the dataset.

---

# Step 8 – Remove Unnecessary Features

The `customerID` column is removed.

This column is only a unique identifier and does not contribute meaningful information for predicting customer churn.

Removing irrelevant features helps reduce model complexity.

---

# Step 9 – Verify Data Types

The dataset is inspected again to ensure that all columns have appropriate data types.

This verification confirms that the preprocessing steps have been successfully completed.

---

# Step 10 – Save the Cleaned Dataset

The cleaned dataset is saved in the `data/processed` directory.

This preserves the original raw dataset while providing a processed version for future analysis and model training.

---

# Outcome

At the end of this phase:

- Hidden missing values were detected.
- Incorrect data types were corrected.
- Missing records were handled.
- Unnecessary columns were removed.
- A cleaned dataset was created.

The dataset is now ready for Exploratory Data Analysis (EDA).

---

# Git Commit

```
git add .
git commit -m "Complete data cleaning and preprocessing"
```

---

# Next Phase

The next stage of the project is **Exploratory Data Analysis (EDA)**.

During EDA, the cleaned dataset will be analyzed to identify customer behaviour, churn patterns, and relationships between different features using statistical analysis and data visualizations.