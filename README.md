# spare-parts-demand-forecasting
A machine learning project to forecast monthly spare-parts demand for a vehicle service business using SQL-sourced service records.

## 📌 Project Overview

This project builds a predictive model to forecast monthly spare-parts demand, enabling better inventory planning and stock management. Service data (~28K rows) was pulled directly from a MySQL database, engineered with time-series features, and used to train and compare multiple regression models.



## 🔧 Tech Stack

- **Language**: Python
- **Libraries**: Pandas, NumPy, Scikit-learn, Seaborn, Matplotlib
- **Database**: SQLAlchemy, MySQL (PyMySQL)

---

## 📊 Models Compared

| Model | MAE | RMSE | R² Score |
|-------|-----|------|----------|
| Linear Regression | ~16.2 | ~19.9 | ~0.890 |
| Ridge Regression (tuned) | ~16.3 | ~20.2 | ~0.887 |
| Gradient Boosting | ~13.9 | ~17.4 | ~0.916 |
| **Random Forest (tuned, log-target)** ✅ | **13.62** | **16.82** | **0.922** |

---

## 🔍 Project Workflow

1. Load service data directly from MySQL database
2. Feature Engineering (v1 → v2): lag values, cyclical month encoding, exponentially-weighted average, part-level historical mean
3. Log-transform target variable to stabilize variance across parts
4. Train-Test Split & Model Training
5. Model Evaluation (MAE, RMSE, R²) across Linear, Ridge, Random Forest, Gradient Boosting
6. Hyperparameter Tuning via Cross-Validation
7. Feature Importance Analysis

---

## 🏆 Best Model Result

- **Model**: Random Forest Regressor (log-transformed target, tuned)
- **R² Score**: 0.922
- **MAE**: 13.62 units/month
- **RMSE**: 16.82

---

## 📁 Dataset

Service records sourced from a MySQL database (`service_data` table), containing invoice dates, vehicle details, and part-level transaction history.

---

## 🚀 Future Improvements

- Segmented modeling per vehicle-model or part category
- Incorporate external signals (holidays, new-vehicle sales, seasonal campaigns)
- Move to weekly forecast granularity
- Ensemble stacking with additional models
- Anomaly detection for unusual demand months
