# 📊 Exploratory Data Analysis (EDA)

## 📖 Overview

Exploratory Data Analysis (EDA) is one of the most important stages in a Data Science project. Before building machine learning models, it is essential to understand the dataset by exploring its patterns, relationships, and characteristics.

The main goal of EDA is to transform raw data into meaningful insights that can support better decision-making and improve model performance.

For this project, EDA was performed on the cleaned IBM Telco Customer Churn dataset to identify the factors that influence customer churn.

---

# 🎯 Objectives

The objectives of this phase are to:

- Understand the distribution of customer churn.
- Explore customer demographic information.
- Analyze customer service usage patterns.
- Identify relationships between different features and churn.
- Detect important trends and business insights.
- Support feature selection for machine learning models.
- Prepare the dataset for feature engineering and model development.

---

# 📂 Dataset Used

The analysis was performed using the cleaned IBM Telco Customer Churn dataset generated during the Data Cleaning and Preprocessing phase.

Dataset Characteristics:

- **Rows:** 7032
- **Features:** 20 Input Features
- **Target Variable:** Churn (Yes / No)

---

# 📌 Analysis Performed

## 1️⃣ Customer Churn Distribution

### Purpose

The first step was to understand the overall distribution of customers who stayed and customers who left the company.

### Visualization

- Count Plot

### Business Question

> How many customers have churned?

### Observation

The dataset contains both churned and non-churned customers. A larger proportion of customers remained with the company, while a smaller proportion left.

This indicates that the dataset is **moderately imbalanced**, which should be considered during model development.

---

## 👨‍👩‍👧 Gender vs Customer Churn

### Purpose

To determine whether customer gender has any influence on churn behaviour.

### Visualization

- Count Plot

### Business Question

> Does gender affect customer churn?

### Observation

The churn distribution appears relatively similar for both male and female customers.

This suggests that gender alone may not be a strong predictor of customer churn.

---

## 👵 Senior Citizen vs Customer Churn

### Purpose

To investigate whether senior citizens are more likely to leave the company's services.

### Visualization

- Count Plot

### Business Question

> Are senior citizens more likely to churn?

### Observation

The analysis indicates that senior citizens tend to have a higher churn rate compared to younger customers.

This customer group may require special retention strategies.

---

## 📄 Contract Type vs Customer Churn

### Purpose

To understand how different contract types influence customer churn.

### Visualization

- Count Plot

### Business Question

> Which contract type has the highest customer churn?

### Observation

Customers with **Month-to-Month contracts** show the highest churn rate.

Customers with **One-Year** and **Two-Year contracts** are more likely to remain with the company.

This suggests that long-term contracts improve customer retention.

---

## 💳 Payment Method vs Customer Churn

### Purpose

To examine whether payment methods influence customer churn.

### Visualization

- Count Plot

### Business Question

> Which payment method is associated with higher churn?

### Observation

Some payment methods appear to have higher churn rates than others.

This insight could help businesses understand customer payment preferences and improve billing strategies.

---

## 🌐 Internet Service vs Customer Churn

### Purpose

To analyze whether different internet service types influence customer churn.

### Visualization

- Count Plot

### Business Question

> Does internet service type affect customer churn?

### Observation

Customers using **Fiber Optic Internet** appear to experience higher churn compared to other internet service types.

Further investigation may help identify the reasons behind this trend.

---

## 📅 Customer Tenure Distribution

### Purpose

To understand how long customers remain with the company.

### Visualization

- Histogram

### Business Question

> How long do customers typically stay?

### Observation

Many customers have relatively short tenures, while a smaller group has remained with the company for several years.

Customer tenure is expected to be an important predictor of churn.

---

## 💰 Monthly Charges Distribution

### Purpose

To analyze the distribution of monthly subscription charges.

### Visualization

- Histogram

### Business Question

> How are monthly charges distributed among customers?

### Observation

Monthly charges vary considerably among customers, reflecting different subscription plans and service packages.

---

## 💵 Total Charges Distribution

### Purpose

To examine the distribution of customers' total billing amounts.

### Visualization

- Histogram

### Business Question

> How much have customers spent overall?

### Observation

The distribution reflects the relationship between customer tenure and monthly subscription charges.

Customers with longer service periods generally have higher total charges.

---

## 📈 Monthly Charges vs Customer Churn

### Purpose

To investigate whether customers paying higher monthly charges are more likely to leave.

### Visualization

- Box Plot

### Business Question

> Do higher monthly charges increase churn?

### Observation

Customers with higher monthly charges tend to show a higher probability of churn.

This may indicate dissatisfaction with pricing or perceived service value.

---

## ⏳ Customer Tenure vs Churn

### Purpose

To compare customer tenure between churned and non-churned customers.

### Visualization

- Box Plot

### Business Question

> Are newer customers more likely to churn?

### Observation

Customers with shorter tenure are more likely to leave the company.

Long-term customers generally show stronger loyalty.

---

## 🔥 Correlation Analysis

### Purpose

To understand relationships among numerical variables.

### Visualization

- Correlation Heatmap

### Observation

The heatmap helps identify positive and negative relationships between numerical variables.

Although correlation does not imply causation, it provides useful insights during feature engineering and model selection.

---

# 💡 Key Business Insights

The Exploratory Data Analysis revealed several important findings:

✅ Month-to-Month contract customers are more likely to churn.

✅ Customers with shorter tenure have a higher risk of leaving.

✅ Higher monthly charges appear to increase customer churn.

✅ Fiber Optic customers show comparatively higher churn.

✅ Senior citizens exhibit a relatively higher churn rate.

✅ Gender does not appear to significantly influence customer churn.

These insights can help businesses design better customer retention strategies and improve service offerings.

---

# 📈 Business Recommendations

Based on the analysis, the following recommendations can be made:

- 🎁 Encourage customers to switch from Month-to-Month contracts to long-term contracts by offering attractive discounts.

- 🤝 Improve customer engagement during the first few months of service to reduce early churn.

- 💰 Review pricing strategies for customers with higher monthly charges.

- 🌐 Investigate customer satisfaction among Fiber Optic users.

- 👵 Develop targeted retention campaigns for senior citizens.

Implementing these strategies could help reduce customer churn and improve long-term customer retention.

---

# ✅ Outcome

At the end of this phase:

- Customer behaviour was successfully explored.
- Important churn patterns were identified.
- Business insights were generated.
- Factors influencing customer churn were discovered.
- The dataset is now ready for Feature Engineering and Machine Learning model development.

---

# 📂 Files Generated

- `03_exploratory_data_analysis.ipynb`
- Visualizations saved in `reports/figures/`
- Business insights documented

---

# 💻 Git Commit

```bash
git add .
git commit -m "Complete exploratory data analysis"
```

---

# 🚀 Next Phase

The next stage of the project is **Feature Engineering**.

During this phase, categorical variables will be encoded, class imbalance will be addressed using **SMOTE**, important features will be selected, and the dataset will be prepared for machine learning model training.

The goal is to create a high-quality feature set that improves prediction accuracy and supports the development of an industry-ready Customer Churn Prediction Platform.