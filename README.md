
# Customer Intelligence & Churn Analytics

A customer analytics project that combines RFM segmentation and machine learning to identify high-value customers, predict churn, and recommend data-driven retention strategies.

---

# Problem Statement

Customer retention is one of the biggest challenges in e-commerce. This UK-based online retailer had no systematic way to distinguish loyal customers from those likely to churn.

The objective of this project was to:

- Identify valuable customer segments using RFM analysis.
- Predict customer churn using machine learning.
- Generate actionable business recommendations to improve customer retention.

---

# Project Structure

```
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
│
└── outputs/
```

---

# Methodology

### 1. Data Loading
- Imported the Online Retail dataset.
- Explored dataset structure and data types.

### 2. Data Cleaning
- Removed missing Customer IDs.
- Removed cancelled orders and returns.
- Removed zero-price transactions.
- Created TotalPrice feature.

### 3. RFM Analysis
Calculated:

- Recency
- Frequency
- Monetary

Applied quantile-based scoring (`pd.qcut`) and created customer segments including:

- VIP
- Loyal Customer
- Potential Loyalist
- At Risk
- Need Attention

### 4. Customer Segmentation
Analyzed customer behaviour using:

- Segment Distribution
- Average Spend
- Frequency vs Monetary relationship

### 5. Churn Prediction
- Created churn labels using a 180-day inactivity threshold.
- Removed Recency from model features to prevent data leakage.
- Trained:
  - Logistic Regression
  - Random Forest
- Compared models using Accuracy, Precision, Recall, F1-score, and Confusion Matrix.

### 6. Model Selection
Selected **Balanced Logistic Regression** because it achieved **93% Recall**, making it the most suitable model for customer retention.

---

# Key Findings

- Need Attention customers had the highest churn rate (62%).
- VIP and Loyal customers showed near-zero churn.
- The model correctly identified **171 of 183 churned customers (93% Recall)**.
- Monetary Value was the strongest predictor of churn.
- False positives present opportunities for proactive customer engagement.

---

# Business Recommendations

### 1. Retain the Need Attention Segment
Launch personalized retention campaigns with targeted offers and loyalty rewards.

### 2. Win Back Predicted Churn Customers
Prioritize high-value customers identified by the model using personalized win-back campaigns.

### 3. Engage False Positive Customers
Use low-cost engagement strategies such as product recommendations and reward points to strengthen customer loyalty.

---

# Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

---

# How to Run

1. Clone the repository.

```
git clone <repository-link>
```

2. Install the required libraries.

```
pip install -r requirements.txt
```

3. Open the notebooks.

```
jupyter notebook
```

4. Run the notebooks in order:

- 01_Data_Loading
- 02_Data_Cleaning
- 03_RFM_Customer_Analysis
- 04_Churn_Prediction_Model

---

# Limitations

- Dataset covers transactions from 2010–2011 only.
- Approximately 25% of transactions without Customer IDs were excluded.
- Churn is defined using a fixed 180-day threshold.
- RFM segmentation simplifies customer behaviour into score buckets, which may not capture all behavioural differences.

---

# About Me

**Vaishnavi Singh**

Aspiring Data Analyst / Business Analyst passionate about transforming customer data into actionable business insights using Python, SQL, machine learning, and data visualization.

If you found this project interesting, feel free to connect with me on LinkedIn or explore my other analytics projects.

