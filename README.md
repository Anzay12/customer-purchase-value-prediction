# 📊 Customer Purchase Value Prediction (Engage-2-Value Kaggle Competition)

## 📌 Project Overview
This project focuses on predicting the **purchase value of a customer session** using multi-session behavioral data from a digital commerce platform.

The objective is to estimate how much a user will spend during a session by analyzing:

- User engagement patterns
- Traffic acquisition sources
- Device & technical attributes
- Geographic behavior
- Historical user activity

This is a **supervised regression machine learning problem**.

---

## 🎯 Problem Statement
Predict:

purchaseValue → Total money spent in a session

The model helps businesses:

- Identify high-value users
- Improve marketing strategies
- Optimize engagement funnels
- Enable data-driven revenue prediction

---

## 📂 Dataset Description
The dataset contains **session-level user interaction data**.

Each row represents a **single session**, while a user may have multiple sessions.

### 🔹 Target Variable

| Column | Description |
|----------|-------------|
| purchaseValue | Total spending during the session |

---

## 🔍 Project Pipeline

---

## 1️⃣ Data Loading & Baseline Model

### 📌 Initial Step
Created a **baseline model** using:

- DummyRegressor

Purpose:
- Establish baseline performance
- Compare ML model improvement later

---

## 2️⃣ Exploratory Data Analysis (EDA)

### Target Distribution Analysis

- Purchase value histogram
- Log transformation behavior
- Skewness detection

📌 Observation:
- Dataset is highly skewed
- Many sessions contain zero purchases

---

### Missing Value Analysis

- Missing value counting
- Missing value visualization
- High missing feature detection

---

## 3️⃣ Feature Engineering ⭐

### 👤 User Level Features

Aggregated behavioral statistics using `userId`:

- userAvgPurchase  
- userTotalPurchase  
- userSessions  
- userPurchaseStd  
- userAvgPageViews  
- userTotalPageViews  
- userAvgHits  
- userTotalHits  

---

### 🧭 Session Level Features

- sessionTotalPageViews  
- sessionTotalHits  
- pages_per_hit  
- session_efficiency  
- engagement_score  

---

### ⏱ Temporal Features

- session_hour  
- session_dayofweek  
- is_weekend  
- is_business_hours  

---

### 📱 Device & Traffic Scores

- device_score  
- traffic_score  

---

## 4️⃣ Feature Selection

Selected optimized feature subsets combining:

- Behavioral metrics
- User aggregation statistics
- Session engagement signals
- Temporal indicators
- Device & marketing signals

---

## 5️⃣ Model Training

### 🌲 Models Used

#### ✅ XGBoost Regressor
- 300 estimators  
- Learning rate = 0.05  
- Max depth = 8  
- Histogram tree method  

---

#### ✅ LightGBM Regressor
- Histogram based gradient boosting  
- Efficient handling of categorical data  

---

#### ✅ HistGradientBoosting Regressor
- Scikit-learn native boosting algorithm  

---

## 6️⃣ Validation Strategy

Used:

GroupKFold Cross Validation

Grouping by:

userId

📌 Benefits:
- Prevents data leakage
- Improves real-world prediction reliability

---

## 📊 Model Performance

| Model | R² Score |
|------------|-------------|
| XGBoost | ⭐ 0.422 |
| LightGBM | Slightly lower |
| HistGradientBoosting | 0.374 |

---

### 🏆 Best Model
XGBoost Regressor

---

## 7️⃣ Hyperparameter Tuning

Used:

RandomizedSearchCV

### Tuned Parameters

- n_estimators  
- learning_rate  
- max_depth  
- subsample  
- colsample_bytree  
- reg_alpha  
- reg_lambda  

Configuration:
- 3-fold Cross Validation  
- 15 random parameter combinations  
- Metric: R² Score  

---

## 8️⃣ Final Model & Predictions

Steps performed:

1. Trained tuned XGBoost on full dataset  
2. Generated predictions on test set  
3. Applied non-negative constraint  
4. Created Kaggle submission file  

---

## 📈 Key Insights

### 💰 Purchase Behavior
- Majority sessions have zero purchases  
- Higher engagement leads to higher spending  

### 📊 User Behavior
- Repeat users spend more  
- Historical purchase predicts future purchase  

### 📱 Device Influence
- Device type affects conversion rates  

### 🌍 Geography Impact
- Spending varies across regions  

---

## ⚠️ Challenges Solved

- High cardinal categorical features  
- Sparse purchase data  
- Multi-session user dependency  
- Noisy behavioral data  

---

## 🛠️ Tech Stack

- Python  
- Pandas  
- NumPy  
- Scikit-learn  
- XGBoost  
- LightGBM  
- Matplotlib  
- Seaborn  
- Kaggle Notebook  

---

## 📁 Output

submission.csv → Final prediction file

---

## 🚀 Future Improvements

- Model ensemble stacking  
- Deep learning session sequence modeling  
- SHAP based explainability  
- Target encoding for high cardinal features  
- Customer lifetime value modeling  

---

## ⭐ Learning Outcomes

- End-to-end ML pipeline development  
- Advanced feature engineering  
- Group-based validation techniques  
- Business-focused ML problem solving  

---

## 👨‍💻 Author
Himanshu
