# Data Understanding

## Overview

Data understanding is the first step in the Data Science lifecycle. Before cleaning, analyzing, or modeling the data, it is important to understand the dataset's structure, features, data types, and overall quality.

The purpose of this phase is to explore the IBM Telco Customer Churn dataset and gain a clear understanding of the available data. This helps identify potential data quality issues and prepares the dataset for the preprocessing stage.

---

# Objectives

The objectives of this stage are to:

- Load the dataset successfully.
- Understand the size and structure of the dataset.
- Identify the available features.
- Examine the data types of each feature.
- Generate summary statistics.
- Check for missing values.
- Identify duplicate records.
- Analyze the target variable (Customer Churn).

---

# Step 1 – Import Required Libraries

The project uses the following Python libraries:

- Pandas
- NumPy

These libraries provide efficient tools for loading, manipulating, and analyzing data.

---

# Step 2 – Load the Dataset

The IBM Telco Customer Churn dataset is loaded into a Pandas DataFrame.

Loading the dataset successfully confirms that the project environment has been configured correctly and that the data is ready for analysis.

---

# Step 3 – Examine the Dataset Size

The shape of the dataset is checked to determine the number of rows and columns.

This provides an overview of the dataset's dimensions and helps estimate the amount of data available for analysis.

---

# Step 4 – View the Feature Names

The list of column names is displayed.

Reviewing the feature names helps understand what customer information is available, such as demographic details, account information, service usage, billing information, and the target variable.

---

# Step 5 – Inspect Data Types

The structure of the dataset is examined using the dataset information.

This step identifies:

- Number of records
- Number of columns
- Data types
- Non-null values
- Memory usage

Understanding the data types is important because machine learning algorithms require numerical input, and categorical variables must later be encoded.

---

# Step 6 – Generate Summary Statistics

Summary statistics are generated for both numerical and categorical variables.

For numerical features, statistics such as:

- Count
- Mean
- Standard deviation
- Minimum value
- Maximum value

are examined.

For categorical features, the unique values and their frequencies are reviewed.

This helps identify unusual values and understand the overall distribution of the data.

---

# Step 7 – Check Missing Values

The dataset is inspected for missing values.

Detecting missing values is an essential step because incomplete data can negatively affect model performance.

At this stage, both visible and hidden missing values are investigated.

---

# Step 8 – Check Duplicate Records

Duplicate records are identified.

Duplicate customer records can introduce bias into machine learning models and should be addressed during preprocessing if necessary.

---

# Step 9 – Analyze the Target Variable

The distribution of the target variable (`Churn`) is examined.

This analysis shows the number of customers who stayed and those who left the company.

Understanding the class distribution helps determine whether the dataset is balanced or imbalanced, which is important when selecting preprocessing techniques such as SMOTE.

---

# Observations

The following observations were made during data understanding:

- The dataset contains customer demographic, service, billing, and account information.
- The target variable is **Churn**, which indicates whether a customer has left the company.
- Both numerical and categorical features are present.
- Further preprocessing is required before machine learning models can be developed.
- Data quality issues, such as incorrect data types and hidden missing values, will be addressed in the next phase.

---

# Outcome

At the end of this stage:

- The dataset structure was successfully understood.
- The available features were identified.
- Data types were examined.
- Missing values and duplicate records were inspected.
- The target variable distribution was analyzed.
- The dataset was prepared for the data cleaning and preprocessing stage.

---

# Git Commit

```bash
git add .
git commit -m "Complete initial data understanding"
```

---

# Next Phase

The next stage of the project is **Data Cleaning and Preprocessing**.

During this phase, hidden missing values, incorrect data types, duplicate records, and unnecessary features will be handled to prepare the dataset for exploratory data analysis and machine learning.