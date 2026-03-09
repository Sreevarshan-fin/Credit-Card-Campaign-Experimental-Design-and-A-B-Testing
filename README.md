

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

 #### Campaign  architecture
 
 <img width="1391" height="507" alt="image" src="https://github.com/user-attachments/assets/a2bb8d02-61cc-4076-9b2b-5328a90d46af" />



To validate the campaign strategy, a controlled experiment was designed.

#### Hypothesis

* **Null Hypothesis (H₀)**  - The new campaign has no impact on customer behavior.

* **Alternative Hypothesis (H₁)**  - The new campaign improves customer engagement and spending.

#### Power Analysis

To ensure the experiment was statistically reliable:

* Significance level (α) = **0.05**
* Statistical power = **0.80**
* Target effect size = **0.4**

Based on these parameters:

**Sample Size ≈ 100 customers per group**

#### Group Assignment

Customers were randomly assigned into:

* **Control Group**  -  Received the existing campaign

* **Test Group** - Received the new credit card campaign

Randomization ensured unbiased comparison between groups.

---

# Results

After running the experiment, the following metrics were observed:

| Metric             | Control Group | Test Group |
| ------------------ | ------------- | ---------- |
| Average Spend      | 221.18        | 235.98     |
| Standard Deviation | 21.36         | 36.66      |


Around 40 out of 100 customers actively began using the credit card after receiving the new campaign offer.

**Conversion Rate (Test Group):** ~40%

---

## Effect Size (Cohen’s d)

To measure the **practical magnitude of the campaign impact**, Cohen’s d was calculated.

#### Difference in Means

```
235.98 − 221.18 = 14.80
```

#### Pooled Standard Deviation

Formula:

```
SD_pooled = √((SD1² + SD2²) / 2)
```

Calculation:

```
SD_pooled = √((21.36² + 36.66²) / 2)
≈ 30
```

#### Cohen’s d

```
d = (Mean_test − Mean_control) / SD_pooled
d = 14.8 / 30 ≈ 0.49
```

#### Interpretation

```
Effect size ≈ 0.49 → Medium effect
```

This indicates the campaign produced a **moderate and practically meaningful increase in customer spending**.

#### Experiment Validation

```
Planned effect size: 0.40
Observed effect size: 0.49
```

Since the observed effect is **higher than the planned detectable effect**, the experiment was **properly powered and the campaign impact is meaningful**.

---

# Experimental Testing

### a) Hypothesis Testing Using Critical Z-Value

##### Z-Score Calculation

Formula:

```python
Z = (mean_test − mean_control) / √((sd_control²/n) + (sd_test²/n))
```

Python implementation:

```python
a = (control_std**2 / sample_size)
b = (test_std**2 / sample_size)

z_score = (test_mean - control_mean) / np.sqrt(a + b)
z_score
```

Result:

```
Z_score = 2.7466
```

##### Critical Z-Value (Right-Tailed Test)

For significance level **α = 0.05**

```python
critical_z = st.norm.ppf(1 - alpha)
critical_z
```

Result:

```
Critical_Z ≈ 1.645
```

##### Decision Rule

```
If Z_score > Critical_Z → Reject H₀
```

```
2.7466 > 1.645
```

✅ **Result:** Reject the null hypothesis.
The campaign produced a **statistically significant uplift**.

---

### b) Hypothesis Testing Using P-Value

##### P-Value Calculation

For a right-tailed test:

```python
p_value = 1 - st.norm.cdf(z_score)
p_value
```

Result:

```
p_value ≈ 0.0030
```

### Decision Rule

```
If p_value < α (0.05) → Reject H₀
```

```
0.003 < 0.05
```

✅ **Result:** Reject the null hypothesis.

The campaign effect is **statistically significant**.

---

# Conclusion

Both methods confirm the same result:

* **Z-Test:** Z_score > Critical_Z
* **P-Value:** p_value < 0.05

Therefore, the **new campaign significantly increased customer spending** compared to the control group.

---
#### C)  Confidence Interval (Very Important)

Instead of only saying the campaign works, show **how much improvement we are confident about**.

## Formula

```
CI = (mean_test − mean_control) ± Z * SE
```

Where

```
SE = √((sd_control²/n) + (sd_test²/n))
```

## Calculation

```
SE = √((21.36²/100) + (36.66²/100))
SE ≈ 5.39
```

For **95% confidence level**:

```
Z = 1.96
```

Margin of error:

```
ME = 1.96 × 5.39 ≈ 10.56
```

Confidence interval:

```
CI = 14.8 ± 10.56
```

```
CI ≈ (4.24 , 25.36)
```

## Interpretation

We are **95% confident** that the campaign increases average customer spending by **₹4.24 to ₹25.36**.

This gives **decision-makers a realistic range of impact**.

---

#### d) Revenue Lift (Business Impact)

Recruiters love **business metrics**.

## Formula

```
Lift (%) = ((Mean_test − Mean_control) / Mean_control) × 100
```

## Calculation

```
Lift = ((235.98 − 221.18) / 221.18) × 100
Lift ≈ 6.69%
```

## Interpretation

The campaign increased **average customer spending by approximately 6.7%**.

This demonstrates a **clear financial impact of the marketing campaign**.

---

# Business Impact

The experiment demonstrates how **data-driven experimentation can guide marketing strategy and reduce decision uncertainty**.

### Key Outcomes

* The new campaign increased **average customer spending by approximately 6.7%** compared to the existing campaign.
* Statistical testing confirmed the improvement is **significant (Z = 2.75, p ≈ 0.003)**.
* The observed **effect size (Cohen’s d ≈ 0.49)** indicates a **moderate practical impact** on customer spending behavior.
* The **95% confidence interval (₹4.24 – ₹25.36)** suggests the campaign consistently increases average spend within this range.

### Strategic Implications

* The campaign successfully improves **credit card engagement and transaction activity**.
* Targeting the **18–25 age segment** presents a strong opportunity for **market expansion**.
* Data-driven experimentation helps **optimize marketing spend and reduce campaign risk**.
* The validated results support **scaling the campaign strategy to a larger customer base** with further optimization.

### Final Recommendation

Based on the experimental results and statistical validation, the **new credit card campaign strategy should be scaled for the 18–25 customer segment**, while continuing to monitor performance and refine targeting for maximum revenue impact.

---

## Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-8CAAE6?style=for-the-badge&logo=scipy&logoColor=white)
![Statsmodels](https://img.shields.io/badge/Statsmodels-5C2D91?style=for-the-badge&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-025E8C?style=for-the-badge&logo=mysql&logoColor=white)

![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge&logo=python&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=for-the-badge&logo=python&logoColor=white)

![Jupyter](https://img.shields.io/badge/Jupyter_Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![A/B Testing](https://img.shields.io/badge/A%2FB_Testing-Statistical_Experimentation-blue?style=for-the-badge)

---



