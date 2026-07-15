# Predicting E-Commerce Customer Churn - Statistical Modeling in R 📉

**A statistics-first study of customer churn: exploratory analysis, hypothesis testing, and logistic regression in R to identify churn drivers and inform marketing strategy - with an honest assessment of what synthetic data can and cannot reveal.**

![R](https://img.shields.io/badge/R-RMarkdown-276DC3?logo=r&logoColor=white) ![Methods](https://img.shields.io/badge/Methods-Hypothesis%20Testing%20%2B%20Logistic%20Regression-blue)
 [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## 💼 Research question
> *What factors predict customer churn in an e-commerce setting, and how can hypothesis testing and regression be used to identify them and guide retention/marketing strategy?*

## 📊 Dataset
**E-commerce Customer Behavior & Purchase** (Kaggle) - a **synthetic** dataset generated with the Faker library, simulating customer demographics, purchase history, payment method, returns, and a binary **churn** label. ~80% of customers are non-churned (class imbalance).

> ⚠️ **Honest note on the data:** because the dataset is *synthetically generated*, the explanatory variables carry little real signal about churn. This project is therefore best read as a **rigorous demonstration of statistical methodology** - and as a candid case study in *recognizing the limits of synthetic data* - rather than a high-accuracy predictive model.

## 🔬 Methodology
- **EDA** - distributions of numerical/categorical features; confirmed the ~80/20 churn class imbalance.
- **Hypothesis testing**  - 
  - **Chi-square tests** of independence between categorical variables and churn → found a significant association for **Payment Method**, none for other categoricals.
  - **t-tests** comparing churned vs. retained customers on `Product Price`, `Customer Age`, etc. → minimal differences.
- **Modeling** - **logistic regression** on price, quantity, total purchase, age, and returns, with **oversampling** to balance the training classes.

## 📈 Results & honest interpretation
- The logistic model achieved **≈50% accuracy and ROC-AUC ≈ 0.5** - i.e. **no better than chance**.
- This is the *correct, expected* outcome for a synthetic dataset with no engineered signal, and the analysis says so plainly.
- **The value is in the process**: a complete, defensible inference workflow (EDA → assumption-aware hypothesis tests → balanced logistic regression → evaluation) and the judgment to **diagnose *why* a model underperforms** instead of overclaiming.

## 🧭 What I'd do with real data
- Use a real behavioral dataset with engagement/recency/frequency/monetary (RFM) features.
- Add tree ensembles (Random Forest / Gradient Boosting) and proper cross-validation.
- Build customer **segments** and tie churn probability to targeted retention offers.

> 💡 For a **predictive** churn/segmentation project on *real* data, see my companion repo **`customer-churn-segmentation-ecommerce`** (Python, UCI Online Shoppers - Random Forest, ROC-AUC ≈ 0.93).

## ▶️ How to run
```r
install.packages(c("tidyverse", "caret", "ROSE", "pROC"))
rmarkdown::render("ecommerce_churn_analysis.Rmd")   # or knit in RStudio
```
Rendered output: [`ecommerce_churn_analysis.html`](ecommerce_churn_analysis.html) · [`report.pdf`](report.pdf)

## 🛠️ Tech stack
`R` · `R Markdown` · `tidyverse` · logistic regression · chi-square & t-tests · oversampling (class imbalance)

---
*Computational Mathematics final project. Related to the `Customer-Segmentation-and-Marketing-Optimization-in-E-Commerce` repo. Demonstrates statistical rigor and honest model evaluation.*


## 📁 Repository contents

| File | What it is |
|---|---|
| `ecommerce_churn_analysis.Rmd` | Full R Markdown source: EDA, hypothesis tests, logistic regression |
| `ecommerce_churn_analysis.html` | Rendered report (download to view) |
| `report.pdf` | Final project report |
| `data/ecommerce_customer_data_large.csv` | Kaggle synthetic e-commerce dataset (250k rows) used in the analysis |

> Note: this repository absorbed `Customer-Segmentation-and-Marketing-Optimization-in-E-Commerce` (now archived) - the two contained the same analysis.
