# Credit Card Campaign Optimization — A/B Testing

![Python](https://img.shields.io/badge/Python-3.11-black)
![Pandas](https://img.shields.io/badge/Pandas-black)
![NumPy](https://img.shields.io/badge/NumPy-black)
![SciPy](https://img.shields.io/badge/SciPy-black)
![Statsmodels](https://img.shields.io/badge/Statsmodels-black)
![Matplotlib](https://img.shields.io/badge/Matplotlib-black)
![Seaborn](https://img.shields.io/badge/Seaborn-black)

---

## 🔹 Overview

A bank aimed to expand its credit card business by identifying the right customer segment and validating a new campaign through controlled experimentation. This project uses **500K+ transaction records** to segment customers, design a statistically rigorous A/B test, and measure campaign impact using hypothesis testing, effect size, and confidence intervals.

---

## 🔹 Business Problem

A bank wanted to launch a new credit card but faced three risks:

| Risk | Description |
|---|---|
| Low adoption | Wrong segment targeted — wasted spend |
| Inefficient marketing | No data-driven segment validation |
| Decision uncertainty | No statistical proof of campaign effectiveness |

**Goal:** Identify the highest-potential customer segment and prove the new campaign works before scaling.

-----


## 🔹 Results at a Glance

| Metric | Value |
|---|---|
| Revenue lift | **6.7%** increase in average spend |
| Z-score | 2.75 (> 1.645 critical) |
| P-value | 0.003 (< 0.05) |
| Cohen's d | 0.49 — medium practical effect |
| 95% Confidence Interval | ₹4.24 – ₹25.36 increase per customer |
| Conversion rate | ~40% in test group |
| Verdict | ✅ Reject H₀ — campaign is effective |

---

## 🔹 Dataset

| Dataset | Records | Contents |
|---|---|---|
| Customers | 1,000 | Demographics, profile |
| Credit Score | 1,004 | Credit scores, limits |
| Transactions | 500,000 | Spend behaviour, categories, payment methods |

---

## 🔹 Phase 1 — EDA & Segmentation

- Cleaned and preprocessed all three datasets — handled missing values and outliers
- Analysed spending behaviour across age groups, categories, and payment methods
- Segmented customers by age — identified 18–25 as highest potential

**Key finding:**

| Segment | Share of Base | Credit Card Adoption | Spending Activity |
|---|---|---|---|
| 18–25 | ~25% | Low | High (Electronics, Fashion, Beauty) |
| 26–40 | ~40% | Medium | Medium |
| 40+ | ~35% | High | Low–Medium |

**Insight:** The 18–25 segment is underserved — strong spenders with low card adoption = high-value untapped opportunity.

---

## 🔹 Campaign  architecture
 
 <img width="1391" height="507" alt="image" src="https://github.com/user-attachments/assets/a2bb8d02-61cc-4076-9b2b-5328a90d46af" />


## 🔹 Phase 2 — Experiment Design

### Hypothesis

| | Statement |
|---|---|
| H₀ | New campaign has no impact on customer behaviour |
| H₁ | New campaign improves spending and engagement |

### Power Analysis

| Parameter | Value |
|---|---|
| Significance level (α) | 0.05 |
| Statistical power | 0.80 |
| Target effect size | 0.40 |
| Required sample size | ~100 per group |

### Group Assignment

| Group | Treatment |
|---|---|
| Control | Existing campaign |
| Test | New credit card campaign |

Customers randomly assigned — ensuring unbiased comparison.

---

## 🔹 Phase 3 — Statistical Testing

<details>
<summary><b>Z-test — critical value method</b></summary>
 
```python
a = (control_std**2 / sample_size)
b = (test_std**2 / sample_size)
z_score = (test_mean - control_mean) / np.sqrt(a + b)
```

| | Value |
|---|---|
| Z-score | 2.7466 |
| Critical Z (α=0.05) | 1.645 |
| Decision | 2.75 > 1.645 → ✅ Reject H₀ |

</details>

<details>
<summary><b>P-value method</b></summary>
 
```python
p_value = 1 - st.norm.cdf(z_score)
```

| | Value |
|---|---|
| P-value | 0.0030 |
| Threshold | 0.05 |
| Decision | 0.003 < 0.05 → ✅ Reject H₀ |

</details>

<details>
<summary><b>Cohen's d — effect size</b></summary>
 
```
Difference in means: 235.98 − 221.18 = 14.80
SD pooled = √((21.36² + 36.66²) / 2) ≈ 30
Cohen's d = 14.8 / 30 ≈ 0.49
```

| Planned Effect Size | Observed Effect Size | Result |
|---|---|---|
| 0.40 | 0.49 | Observed > planned — experiment properly powered ✅ |

**Interpretation:** Medium practical effect — campaign produced a meaningful increase in spending.

</details>

<details>
<summary><b>Confidence interval</b></summary>
 
```
SE = √((21.36²/100) + (36.66²/100)) ≈ 5.39
ME = 1.96 × 5.39 ≈ 10.56
CI = 14.8 ± 10.56 → (4.24, 25.36)
```

**Interpretation:** We are 95% confident the campaign increases average spend by **₹4.24 to ₹25.36** per customer.

</details>

<details>
<summary><b>Revenue lift</b></summary>
 
```
Lift = ((235.98 − 221.18) / 221.18) × 100 ≈ 6.7%
```

The campaign increased average customer spending by **6.7%** over the control group.

</details>

---

## 🔹 Business Impact

- **6.7% revenue lift** confirmed statistically — not just observed by chance
- **~40% conversion rate** in test group — 40 out of 100 customers activated the card
- **95% CI of ₹4.24–₹25.36** gives decision-makers a realistic range to forecast returns
- Results support **full-scale rollout** of the campaign to the 18–25 segment

**Recommendation:** Scale the new campaign to the 18–25 segment. Continue monitoring spend lift and conversion rate post-rollout for further optimisation.

---

## 🔹 Project Structure
```
ab-testing-campaign/
│
├── notebooks/
│   ├── 01_eda_segmentation.ipynb      # EDA and age group analysis
│   └── 02_ab_testing.ipynb            # Experiment design and testing
│
├── data/                              # Raw datasets (not included — NDA)
├── requirements.txt
├── README.md
└── .gitignore
```

---

## 🔹 Challenges

- **Sample size constraint** — 100 per group is small; power analysis upfront ensured the test was sensitive enough to detect the target effect
- **One-tailed vs two-tailed** — chose right-tailed test since the hypothesis was directional (improvement, not just difference)
- **Effect size interpretation** — Cohen's d alone doesn't tell the business story; pairing it with revenue lift made the result actionable

  -----

  ## 🔹 Future Improvements

- **Expand sample size** — current test used ~100 per group; scaling to 500+ would increase statistical power and detect smaller effect sizes more reliably
- **Multi-variant testing (A/B/C)** — test multiple campaign variants simultaneously to find the optimal message, offer, and channel combination
- **Automated monitoring pipeline** — track post-rollout metrics (spend, conversion, churn) continuously to detect campaign decay over time
- **Segment drift monitoring** — monitor whether the 18–25 segment behaviour shifts seasonally or over time using PSI/CSI-style checks
- **Sequential testing** — replace fixed-horizon testing with sequential methods to allow early stopping when significance is reached, reducing wasted spend
- **Bayesian A/B testing** — complement frequentist approach with Bayesian inference to quantify probability of campaign being better, not just significance
- **Long-term impact tracking** — measure 3–6 month spend retention, not just immediate uplift, to assess true campaign lifetime value
- **Subgroup analysis** — break down results by gender, region, and spending category to identify which sub-segments drive the most lift

  ----

## Author

**Sree Varshan**

Data Science & AI | Machine Learning | Financial Domain

