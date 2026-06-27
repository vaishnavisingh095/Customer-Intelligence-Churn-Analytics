# Customer Intelligence & Churn Analytics
### End-to-End Customer Analytics | RFM Segmentation + 
### Machine Learning Churn Prediction

> "Most businesses treat all customers the same. 
>  This project proves why that's a costly mistake."

---

## 🎯 Project Overview

This project analyzes **541,909 retail transactions** from a 
UK-based online gift retailer to answer three business questions:

1. **Who are our most valuable customers?**
   → RFM segmentation across 4,338 customers
   
2. **Which customers are about to leave?**
   → Machine learning churn prediction (93% Recall)
   
3. **What should the business do about it?**
   → Data-driven retention recommendations

**Target Roles:** Data Analyst | Business Analyst | 
                  CRM Analyst | Marketing Analyst

---

## 💡 Problem Statement

Customer retention is one of the biggest challenges in 
e-commerce. This retailer had no systematic way to 
distinguish loyal customers from those likely to churn — 
meaning marketing budget was being spent without knowing 
which customers actually needed attention.

**This project solves that** by combining behavioral 
segmentation with predictive modeling to tell the business 
exactly WHO to target, WHEN, and WHY.

---

## 🧠 Key Analytical Decisions (and Why I Made Them)

> This section shows the thinking behind the project — 
> not just what was done, but why each decision was made.

**Why 180-day churn threshold?**
The dataset's recency distribution showed 75% of customers 
return within 142 days. I set 180 days as the threshold 
to give customers a reasonable buffer beyond typical 
repurchase behavior — strict enough to flag genuinely 
inactive customers, not just slow returners.

**Why remove Recency from model features?**
Recency was used to directly CREATE the churn label 
(Recency > 180 = Churned). Including it as a model feature 
would be data leakage — the model would be given the answer 
key instead of learning real patterns.

**Why choose Logistic Regression over Random Forest?**
Random Forest had higher overall accuracy (74% vs 65%), 
but Logistic Regression caught 93% of churned customers 
vs Random Forest's 48%. In churn prediction, missing a 
churned customer (false negative) costs more than a false 
alarm (false positive) — so Recall matters more than 
Accuracy. Additionally, false positives represent customers 
who receive retention offers anyway, potentially generating 
additional revenue rather than pure waste.

**Why use class_weight='balanced'?**
The dataset had 80% active vs 20% churned customers. 
Without balancing, the model defaulted to predicting 
"Active" for everyone — achieving 79% accuracy while 
catching zero churned customers. This is the Accuracy 
Paradox — high accuracy, zero business value.

---

## 📁 Project Structure

Customer-Intelligence-Churn-Analytics/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── data/
│   ├── OnlineRetail.xlsx
│   ├── online_retail_clean.csv
│   └── customer_rfm_analysis.csv
│
├── notebooks/
│   ├── 01_Data_Loading.ipynb
│   ├── 02_Data_Cleaning.ipynb
│   ├── 03_RFM_Customer_Analysis.ipynb
│   └── 04_Churn_Prediction_Model.ipynb
│
├── images/
│   ├── segment_distribution.png
│   ├── frequency_vs_monetary.png
│   ├── churn_by_segment.png
│   ├── feature_importance.png
│   └── confusion_matrix.png

---

## 🔬 Methodology

### 1. Data Cleaning
- Removed rows with missing Customer IDs (guest checkouts 
  — unusable for customer-level analysis)
- Removed negative quantities (product returns)
- Removed zero-price transactions (data entry errors)
- Result: 397,884 clean rows from 541,909 original 
  (~26% removed, all justified)

### 2. RFM Feature Engineering
Created three behavioral features per customer:
- **Recency** → Days since last purchase 
  (using dataset snapshot date, not today's date — 
  to keep analysis within the dataset's own time period)
- **Frequency** → Count of unique invoices
- **Monetary** → Sum of Quantity × UnitPrice

### 3. RFM Scoring & Segmentation
- Applied quantile-based scoring (pd.qcut) — 5 buckets 
  per metric
- Recency scoring reversed (lower days = better score)
- 7 named segments: VIP, Loyal, Potential Loyalist, 
  At Risk, Need Attention

### 4. Churn Prediction
- Churn label: Recency > 180 days = Churned (1)
- Features used: Frequency, Monetary, AvgOrderValue
- Recency removed to prevent data leakage
- Models: Logistic Regression + Random Forest
- Both trained with class_weight='balanced' to handle 
  80/20 class imbalance

### 5. Model Evaluation & Selection
Evaluated using Accuracy, Precision, Recall, F1-Score, 
and Confusion Matrix. Selected Logistic Regression 
for highest Recall (93%) — aligned with business goal 
of catching as many churned customers as possible.

---

## 📊 Key Findings

| Finding | Detail |
|---------|--------|
| Highest churn segment | Need Attention (62% churn rate) |
| Safest segments | VIP + Loyal (~0% churn) |
| Churned customers caught | 171 out of 183 (93% Recall) |
| Strongest churn predictor | Monetary Value (~45% importance) |
| False positive opportunity | 292 active customers flagged → retention offer candidates |
| Revenue insight | Mean spend ₹2,054 vs median ₹674 → right-skewed, few customers drive disproportionate revenue |

---

## 💼 Business Recommendations

### 1. Urgent: Retain Need Attention Segment (62% churn)
Launch personalized retention campaigns immediately — 
targeted coupons, early product access, loyalty rewards. 
Every day without action increases permanent loss risk.

### 2. Win-Back: Target 171 Model-Identified Churned Customers
Prioritize by Monetary value — highest spenders first. 
Personalized "We miss you" emails with exclusive offers. 
Even recovering 30% represents significant revenue.

### 3. Opportunity: Engage 292 False Positive Customers
These active customers show behavioral patterns similar 
to churned customers. A low-cost engagement campaign 
(recommendations, reward points) now prevents them from 
becoming actual churned customers later — turning a 
model limitation into a proactive business opportunity.

---

## 🛠️ Technologies Used

| Tool | Purpose |
|------|---------|
| Python | Core analysis |
| Pandas | Data manipulation |
| NumPy | Numerical operations |
| Matplotlib + Seaborn | Visualizations |
| Scikit-learn | ML models + evaluation |
| Jupyter Notebook | Development environment |

---

## 🚀 How To Run

1. Clone the repository
git clone <repository-link>

2. Install required libraries
pip install -r requirements.txt

3. Run notebooks in order:
   01_Data_Loading → 02_Data_Cleaning → 
   03_RFM_Customer_Analysis → 04_Churn_Prediction_Model

---

## ⚠️ Limitations

- Dataset covers 2010–2011 only — methodology remains 
  valid and replicable on current data
- ~25% of transactions excluded due to missing Customer IDs 
  (guest checkouts — not usable for customer-level analysis)
- Churn threshold (180 days) is based on data distribution, 
  not confirmed business definition
- RFM scoring groups customers into 5 buckets — two 
  customers with identical scores may still behave 
  differently in reality

---

## 👩‍💻 About Me

**Vaishnavi Singh**
Aspiring Data Analyst | Business Analyst

Passionate about transforming raw customer data into 
decisions that actually matter to a business. This project 
reflects my approach: understand the business problem first, 
make every analytical decision with a clear reason, and 
communicate findings in plain language.

📧 vaishnavisingh7989@gmail.com
💼 https://www.linkedin.com/in/vaishnavisingh0/
