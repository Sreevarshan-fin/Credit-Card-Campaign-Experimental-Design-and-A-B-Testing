

# Credit Card Campaign Optimization using A/B Testing

A practical experiment-driven approach using **behavioral transaction data and statistical validation** to design and evaluate a credit card campaign for young customers.

This project demonstrates how **data analysis, segmentation, and hypothesis testing** can support data-driven marketing decisions.

---

# Problem Statement

A growing bank wanted to expand its credit card business and increase market penetration.

However, launching a new credit card campaign without proper targeting could lead to:

* Low adoption rates
* Inefficient marketing spend
* Increased credit risk

The key challenge was identifying **the right customer segment** and validating whether a new campaign strategy could significantly improve customer engagement.

The goal was to use **data-driven experimentation** instead of assumptions to design and validate the campaign.

---

# Dataset

The analysis used three related datasets:

**Customers Dataset**

* 1,000 records
* Customer demographics and profile information

**Credit Score Dataset**

* 1,004 records
* Credit scores and credit limit details

**Transactions Dataset**

* 500,000 transaction records
* Transaction amount, category, payment method

These datasets allowed linking **customer demographics, credit behavior, and spending activity**.

---

# Solution Approach

The project followed **two main phases**.

## 1. Exploratory Data Analysis (EDA)

Initial analysis focused on understanding customer behavior.

Steps performed:

* Data cleaning and preprocessing
* Handling missing values and outliers
* Behavioral spending analysis
* Customer segmentation by age group

Key insights:

* Customers aged **18–25 represent ~25% of the customer base**
* This segment shows **lower credit history and credit card adoption**
* However, they demonstrate **strong spending activity in categories like Electronics, Fashion, and Beauty**

This suggested a potential **untapped opportunity for targeted credit card campaigns**.

---

## 2. Experiment Design (A/B Testing)

To validate the campaign strategy, a controlled experiment was designed.

### Hypothesis

**Null Hypothesis (H₀)**
The new campaign has no impact on customer behavior.

**Alternative Hypothesis (H₁)**
The new campaign improves customer engagement and spending.

### Power Analysis

To ensure the experiment was statistically reliable:

* Significance level (α) = **0.05**
* Statistical power = **0.80**
* Target effect size = **0.4**

Based on these parameters:

**Sample Size ≈ 100 customers per group**

### Group Assignment

Customers were randomly assigned into:

**Control Group**

* Received the existing campaign

**Test Group**

* Received the new credit card campaign

Randomization ensured unbiased comparison between groups.

---

# Results

After running the experiment, the following metrics were observed:

| Metric             | Control Group | Test Group |
| ------------------ | ------------- | ---------- |
| Average Spend      | 221.18        | 235.98     |
| Standard Deviation | 21.36         | 36.66      |

**Conversion Rate (Test Group):** ~40%

### Effect Size

Cohen's d was calculated to measure practical impact.

Effect size ≈ **0.49**

Interpretation:

**Medium practical impact**

### Hypothesis Testing

A **two-sample Z-test** was performed.

Results:

* p-value < 0.05
* Null hypothesis rejected

Conclusion:

The new campaign produced a **statistically significant improvement in customer spending behavior**.

---

# Business Impact

The experiment demonstrates how **data-driven experimentation can guide marketing strategy**.

Key outcomes:

* Increased credit card activation and usage
* Better targeting of high-potential customer segments
* Reduced marketing risk through statistical validation
* Evidence-based campaign design

Based on the results, the campaign strategy can be **scaled for the 18–25 customer segment** with further optimization.

---
Tech Stack:
Python (Pandas, NumPy, SciPy, Statsmodels)
SQL
Matplotlib / Seaborn
Jupyter Notebook
A/B Testing Framework

---



