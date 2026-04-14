# Network Traffic Classification and Intrusion Detection (CIC-IDS2017)

[cite_start]This repository contains a comprehensive **multi-class classification** solution for cybersecurity using the **CIC-IDS2017** dataset[cite: 1, 118]. [cite_start]The project evaluates and compares the performance of two ensemble algorithms—**XGBoost** and **Random Forest**—through a rigorous experimental design with statistical validation[cite: 2, 119].

## 📌 Project Overview
[cite_start]The objective is to identify whether network traffic is legitimate (Benign) or belongs to a specific attack category (DDoS, PortScan, Bot, Infiltration, etc.)[cite: 6, 124]. [cite_start]The model aims to support automated traffic management and real-time alerting within an **Intrusion Detection System (IDS)**[cite: 7, 125].

## 📊 Dataset: CIC-IDS2017
[cite_start]The dataset features a **massive class imbalance** (80.32% Benign traffic), which makes Accuracy a misleading metric[cite: 15, 16, 136]. [cite_start]Therefore, **Macro F1-Score** was selected as the primary metric to ensure that minority but critical classes (like *Infiltration*) are correctly detected[cite: 17, 22, 137, 147].

### Data Composition
- **Benign:** 80.32%
- **DoS Hulk:** 8.13%
- **PortScan:** 5.62%
- **DDoS:** 4.53%
- Others (Bot, Infiltration, Web Attacks, etc.): <1%

## 🛠️ Methodology and Experimental Design
A workflow with high statistical rigor was implemented:
1. [cite_start]**Preprocessing:** Cleaning of multicollinearity, null values, and zero variance[cite: 5, 123]. [cite_start]Numerical features were normalized using `StandardScaler`[cite: 57, 227].
2. [cite_start]**Data Partitioning:** 15% reserved for the final **Test Set** and 85% for development (Cross-Validation)[cite: 54, 56, 223, 225].
3. [cite_start]**Repeated Stratified K-Fold:** 5 folds repeated 6 times (total of 30 independent runs per model) to ensure result stability[cite: 59, 60, 229, 230].
4. **Hypothesis Testing:**
   - [cite_start]**Shapiro-Wilk Test:** To verify the normality of performance differences[cite: 41, 196].
   - [cite_start]**Paired t-Student Test:** To determine if there is a statistically significant superiority of one model over the other[cite: 47, 208].

## 🤖 Models and Hyperparameters
### XGBoost (Extreme Gradient Boosting)
- **n_estimators:** 150
- **learning_rate:** 0.08
- **max_depth:** 6
- **subsample / colsample_bytree:** 0.8

### Random Forest
- **n_estimators:** 200
- **max_depth:** 17
- **class_weight:** balanced

## 📈 Results and Statistical Conclusion
[cite_start]After 30 iterations, the statistical analysis yielded a **p-value < 0.05** ($9.21 \times 10^{-16}$), leading to the rejection of the null hypothesis of equality[cite: 66, 67].

**Conclusion:** **XGBoost** is statistically superior to Random Forest for this dataset.

| Metric (Mean) | XGBoost | Random Forest |
| :--- | :--- | :--- |
| **Validation Macro F1** | **0.8308** | 0.7545 |
| **Std. Deviation** | 0.0199 | 0.0252 |


## 💻 Requirements
To run the notebook `Clasificacion-CIC-IDS-2017.ipynb`, it is recommended to use a **CUDA-enabled GPU** and the following libraries:
- `numpy`
- `pandas`
- `scikit-learn`
- `xgboost`
- `seaborn`
- `matplotlib`

---
[cite_start]*Developed by Christian Gómez Magdaleno, Noe Israel Felipe Perez, and Andrea Guadalupe Garcia Oñate (University of Guanajuato).* [cite: 1, 114, 115]
