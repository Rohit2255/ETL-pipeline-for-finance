# 🚀 Day 12 – ETL Pipeline for Stock Market Data (TSLA)

This project is part of my **#100DaysOfFinanceDataScience** challenge where I build one project every day to sharpen my data science and finance domain skills.

For Day 12, I focused on building an **ETL (Extract, Transform, Load) pipeline** using Python to process stock market data (Tesla Inc. – TSLA) and perform **stock price movement classification** using various machine learning models including **XGBoost**.

---

## 📌 Problem Statement

Build an ETL pipeline to:
- Load and clean raw TSLA stock data.
- Engineer technical indicators (features) from historical prices.
- Create a target label indicating price movement (`UP` or `DOWN`).
- Train classification models (Logistic Regression, Random Forest, XGBoost).
- Evaluate performance and tune hyperparameters (handling class imbalance, SMOTE, etc).

---

## 📊 Data Source

- **Dataset**: TSLA_raw.csv
- **Frequency**: Daily (Business Days)
- **Features Included**: Open, High, Low, Close, Volume
- **Generated Features**: Moving Averages, RSI, MACD, etc.

---

## 🧪 Project Pipeline

### 1. 📥 Extraction
- Loaded raw TSLA CSV data using `pandas`.
- Converted all price/volume columns to numeric.
- Generated `Date` index from a starting date assuming business days.

### 2. 🔁 Transformation
- Computed technical indicators (SMA, RSI, MACD).
- Defined binary target: `1` for price up (next day), `0` for price down or unchanged.
- Removed `NaN` values from rolling computations.

### 3. 📤 Load & Modeling
- Split into train-test sets (70-30 split).
- Tried baseline Logistic Regression & Random Forest.
- Applied **SMOTE** for class balancing.
- Tuned **XGBoost Classifier** using `scale_pos_weight`.

---

## ⚙️ Tech Stack & Libraries

- `pandas`, `numpy`, `scikit-learn`
- `xgboost`, `matplotlib`, `seaborn`
- `imblearn` (for SMOTE)

---

## 📈 Model Performance (Final XGBoost Model)

| Metric        | Score  |
|---------------|--------|
| **Accuracy**  | 0.49   |
| **Precision** | 0.54 (class 1) |
| **Recall**    | 0.83 (class 1) |
| **Confusion Matrix** |  
|               | Pred 0 | Pred 1 |
|---------------|--------|--------|
| **Actual 0**  | 0      | 17     |
| **Actual 1**  | 4      | 20     |

> ⚠️ Model tends to over-predict upward movement. We plan to balance recall vs. precision better in future improvements.

---

## 📌 Key Takeaways

- ETL pipelines are essential for automating real-time data processing and modeling.
- Imbalanced datasets can heavily affect model performance — **class weights and SMOTE help**.
- XGBoost performed better recall-wise but still lacks generalization — needs further tuning and more data.

---

## 📅 What's Next?

- Deploy the pipeline as a **Streamlit** dashboard.
- Add real-time stock feed via API.
- Tune models with time series cross-validation.
- Add confidence intervals and backtesting with trading signals.

---

## 🙋‍♂️ About Me

I’m **Rohit Kumar Yadav**, a data science learner combining my love for finance and machine learning through a **100 Days, 100 Finance Projects** challenge.

📌 Connect with me:  
🔗 [LinkedIn – Rohit Kumar Yadav](https://www.linkedin.com/in/rohit-kumar-yadav-b97360194/)  
💻 [GitHub – rohit2255](https://github.com/rohit2255)

---

## ⭐ Project Badge

`#Day12 #FinanceDataScience #ETLPipeline #StockMarket #XGBoost #DataScience #100DaysChallenge #Python`

---

## 📁 How to Use

```bash
# Clone the repo
git clone https://github.com/rohit2255/Finance-DS-100Days.git

# Go to the project folder
cd Day12_ETL_Pipeline_TSLA

# Install dependencies
pip install -r requirements.txt

# Run the pipeline
python etl_pipeline.py
