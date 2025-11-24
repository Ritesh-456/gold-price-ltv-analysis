## **Gold Price Forecasting and Loan-to-Value (LTV) Risk Modelling Using Machine Learning and Deep Learning Techniques**


##  🏦 **1. Introduction**

Gold-backed lending is one of the fastest-growing secured loan sectors in India, with Non-Banking Financial Companies (NBFCs) and banks relying heavily on gold price stability to ensure the safety of their collateralized portfolios. However, gold prices exhibit high sensitivity to global market conditions, macroeconomic indicators, and commodity price fluctuations. Sudden declines in gold value directly increase the Loan-to-Value (LTV) ratio, exposing lenders to elevated default and margin-call risk.

To address this challenge, this project develops a comprehensive data-driven risk assessment and forecasting framework capable of predicting future gold prices, analyzing their impact on loan portfolios, and explaining the underlying drivers behind these predictions.

---

## ❗**2. Problem Statement**

Financial institutions face significant operational and credit risks when gold prices exhibit volatility.  
Key questions addressed in this research include:

- 🔹**How will gold prices move in the next 30–90 days?**  
- 🔹**What is the expected LTV position of a loan portfolio under normal and stressed market conditions?**  
- 🔹**Which macroeconomic factors most strongly influence gold price trends?**  
- 🔹**How can machine learning models provide interpretable and actionable insights?**

The goal is to build an end-to-end analytical system that integrates data preprocessing, feature engineering, ML forecasting, explainability, and real-time analytics.

---

## 🎯**3. Objectives**

### **Primary Objectives**
-  📈 Forecast short-term gold price movements using classical, machine learning, and deep learning models.  
-  🧮 Estimate future LTV ratios for a synthetic gold loan portfolio.  
-  🚨 Identify high-risk loans under multiple stress scenarios.  
-  🔍 Provide explainability of predictions using SHAP values.  

### **Secondary Objectives**
-  🖥 Build a fully functional multi-tab Streamlit dashboard for interactive risk monitoring.  
- ⚡ Deploy GPU-optimized models for improved training and inference performance.

---

##  🔬 **4. Methodology**

The project follows a structured data science lifecycle.

---

### **4.1 Data Acquisition**

Three heterogeneous datasets were collected:

- Daily MCX India gold prices (2014–2025)  
- Gold ETF and macroeconomic indicators (USO, USD Index, S&P 500, Dow Jones, commodity prices)  
- World Gold Council historical gold data (1978–2023)  

---

### **4.2 Data Processing and Standardization**

- Cleaning missing and inconsistent values  
- Converting date fields to uniform time-index  
- Merging multi-source datasets  
- Interpolating missing macroeconomic indicators  
- Generating a unified daily dataset with **1659 observations × 98 features**

---

### **4.3 Feature Engineering**

Advanced time-series engineering was performed:

- ⏱ Lag features: **1, 2, 7, 14, 30 days**  
-  📉 Moving averages: **MA7, MA14, MA30, MA60**  
- 📊  Rolling volatility: **STD7, STD14, STD30, STD60**  
-  🔄 Trend direction flags  
-  📅 Date-derived features: **Year, Month, Quarter, Day-of-Week**  
-  🌍 Cross-market features from **USO, USD Index, GDX, Silver, Oil, Bond yields**

This enriched feature space significantly improved model predictive capacity.

---

##  🤖 **5. Modelling Approach**

---

### **5.1 Classical Models**
- **Linear Regression**  
  - Served as a baseline.  
  - Demonstrated limitations due to non-linear relationships.

---

###  🌲 **5.2 Machine Learning Models**

#### **Random Forest Regressor**
- Captures non-linear interactions.  
- Provides feature-level interpretability.

#### ⚡ **XGBoost Regressor (GPU Accelerated)**
- Trained using **NVIDIA RTX 3050 (CUDA)**  
- Delivered superior generalization  
- Exported to **JSON format** to ensure compatibility with XGBoost ≥ 3.1  
- Used for **SHAP explainability**

---

###  🧠 **5.3 Deep Learning**

#### **LSTM (Long Short-Term Memory) Network**
- Input sequence length: **30 days**  
- 2-layer architecture with **128 hidden units**  
- Learned temporal dependencies effectively  
- Produced **30–90 day forward forecasts**

All models were evaluated using **RMSE, MAE, and R²**.

---

##  📊 **6. Portfolio LTV Risk Modelling**

A synthetic loan portfolio was generated with:

- Gold purity  
- Loan amount  
- Disbursal date  
- Principal-to-purity-adjusted gold value  
- Historical gold price at issuance  

### **Risk Metrics Computed**
- **Current LTV**  
- **Forecasted LTV** (using ML predictions)  
- **Stress scenario LTVs:** −5%, −10%, −20% gold price drop  
- **High-risk loan detection**

This enabled lenders to anticipate **margin call triggers**.

---

##  🧮 **7. Explainability & Model Interpretation**

To ensure transparency and regulator-friendly modelling:

### **SHAP (Shapley Additive Explanations)** was used.

Key drivers revealed:

- **USD Index**  
- **USO Close**  
- **S&P500 Close**  
- **GDX Gold Miner ETF**  
- **Lagged Adj Close values**

SHAP ensured the system is interpretable and suitable for financial environments requiring auditability.

---

##  🖥 **8. Dashboard Implementation**

A multi-tab **Streamlit** application was developed to integrate all analytical components.

### 📌 **Tab 1 — LTV Analysis**
- Portfolio distribution  
- LTV metrics  
- Stress-test evaluation  
- Risk flagging

### 📌 **Tab 2 — ML Forecast & Prediction**
- Single-day predictions (**RF / XGB / LSTM**)  
- Editable input panel  
- 30–90 day LSTM forward forecast  

### 📌 **Tab 3 — Explainability**
- SHAP summary plot  
- Feature importance rankings  

This dashboard acts as a prototype **risk analytics tool** for fintechs, NBFCs, and banks.

---

##  📝 **9. Results**

- **XGBoost** produced the strongest predictive performance.  
- **LSTM** successfully captured long-term temporal patterns and provided stable forecasts.  
- **SHAP** validated that the model relies on meaningful macroeconomic indicators.  
- Stress testing correctly highlighted loans with potential LTV breaches.

---

##  📝 **10. Conclusion**

This project demonstrates a complete **real-world financial risk modelling system** integrating:

- Multi-source data  
- Advanced engineered features  
- Machine learning & deep learning approaches  
- Model explainability  
- Portfolio stress testing  
- Dashboard deployment  

It accurately mirrors workflows used by **NBFCs, banks, and fintech companies** that depend on gold-backed lending.

---

##  🚀 **11. Future Enhancements**

- Integrate **real-time MCX/live gold price API**  
- Add **ARIMA / SARIMA** for statistical comparison  
- Deploy dashboard on cloud with automated updates  
- Implement **reinforcement learning** for dynamic LTV thresholds  
- Expand modelling to **multi-collateral risk systems**  
- Introduce **PostgreSQL database** for portfolio storage  

---

##  🛠 **12. Technologies Used**

- **Pytho, Pandas, NumPy**
- **Scikit-learn, XGBoost, PyTorch**  
- **SHAP, Statsmodels**  
- **Streamlit**  
- **Matplotlib, Seaborn**  
- **CUDA GPU (RTX 3050)**  
- **Jupyter Notebooks**

---

## 📂 **13. Repository Structure**

```plaintext
gold-price-ltv-analysis/
│
├── Dataset/
├── models/
├── outputs/
├── Notebooks/
│
├── app.py
├── lstm_model_def.py
├── model_loader.py
├── requirements.txt
└── README.md
```