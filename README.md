# Weather Trend Forecasting Project

## Overview

This project analyzes global daily weather data and forecasts future temperature trends using time-series modeling and machine learning techniques. The goal is to demonstrate a complete data science workflow including preprocessing, exploratory analysis, forecasting, anomaly detection, and feature importance interpretation.

---

## Dataset

**Global Weather Repository (Kaggle)**  
Contains worldwide daily weather measurements across multiple cities and countries including temperature, precipitation, humidity, and pressure.

**Target variable:** `temperature_celsius`  
**Time column:** `last_updated`

---

## Project Pipeline

### 1. Data Cleaning & Preprocessing

- Converted `last_updated` to datetime and set as index
- Sorted chronologically for time-series analysis
- Handled missing values using forward/backward fill
- Removed outliers using IQR method (temperature in Celsius only)
- Standardized numeric features using StandardScaler

---

### 2. Exploratory Data Analysis (EDA)

Performed visualization and statistical analysis:

- Temperature trend over time
- Precipitation trend
- Correlation heatmap (numeric features only)
- Monthly seasonal patterns

**Key Insight:**  
The dataset exhibits seasonal periodicity, making it suitable for seasonal time-series forecasting models.

---

### 3. Forecasting Models

Two forecasting models were implemented and compared:

#### SARIMA
Captures trend and seasonality using autoregressive seasonal structure.

#### Prophet
Attempts to capture long-term seasonal patterns and trend decomposition but produced significantly higher prediction error compared to SARIMA.

Evaluation Metrics:
- MAE (Mean Absolute Error)
- RMSE (Root Mean Squared Error)

---

## Results Summary

| Model | MAE | RMSE |
|------|----|----|
| **SARIMA** | **0.8827** | **1.0315** |
| Prophet | 38.7284 | 44.7535 |
| Ensemble | 19.3786 | 22.3830 |

### Selected Final Model: **SARIMA**

SARIMA significantly outperformed Prophet and the Ensemble model.  
This indicates the dataset contains strong short-term seasonal structure that is best captured using autoregressive seasonal modeling rather than additive decomposition.

---

### Key Findings

- Temperature anomalies appear in clustered spikes rather than isolated points
- Countries with lowest temperature variability:  
  Kiribati, Cote d'Ivoire, Maldives, Marshall Islands, Tuvalu
- Air quality indicators correlate with temperature fluctuations
- Most influential predictors of temperature:

  - temperature_fahrenheit
  - feels_like_celsius
  - feels_like_fahrenheit
  - wind_degree
  - moon_illumination

---

### Why SARIMA Was Chosen

SARIMA was selected because:

- Lowest forecasting error (MAE & RMSE)
- Captures repeating seasonal cycles effectively
- More stable predictions compared to Prophet
- Ensemble improved stability but not accuracy

---

## Advanced Analysis

### Anomaly Detection
Isolation Forest used to detect unusual weather conditions (extreme temperature events).  
Anomalies were not rare but occurred in clustered spikes indicating short abnormal weather phases.

### Feature Importance
Random Forest regression identified meteorological variables influencing temperature variation.

### Climate Analysis
Country-level temperature variability analyzed using standard deviation to observe regional climate stability differences.

---

## Additional Analysis

- Ensemble forecasting improved prediction stability but not accuracy
- Air quality metrics showed relationship with temperature patterns
- Geographic patterns revealed regional climate consistency differences

---

## Practical Applications

- Energy demand planning
- Agriculture risk prediction
- Climate monitoring
- Smart city weather adaptation
- Event planning and logistics

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib & Seaborn
- Scikit-learn
- Statsmodels (SARIMA)
- Prophet
- Time-Series Ensemble Modeling
- Environmental Correlation Analysis
- Geographical Climate Comparison

---

## How to Run

1. Install dependencies

pip install pandas numpy matplotlib seaborn scikit-learn statsmodels prophet

2. Place dataset inside project folder

data/GlobalWeatherRepository.csv

3. Run notebook cells in order:

- Data Cleaning
- EDA
- Forecasting
- Advanced Analysis

---

## Project Structure

```
weather-trend-forecasting/
│
├── data/
│   └── GlobalWeatherRepository.csv
│
├── notebooks/
│   └── Weather_Trends_Forecasting.ipynb
│
├── images/
│   ├── Anomaly_Detection.png
│   ├── Feature_Importance.png
│   └── Temperature_Forecast.png
│
├── requirements.txt
└── README.md
```

---

## PM Accelerator Mission

The PM Accelerator program is designed to help students and early-career professionals transition into technology careers by developing practical, industry-relevant skills and career readiness. The program focuses on bridging the gap between academic learning and real-world job expectations through hands-on projects, mentorship, and portfolio development. Its goal is to prepare participants to secure roles in competitive tech industries and grow into impactful professionals.

---

## Reproducibility

Results may vary slightly due to stochastic machine learning algorithms (Random Forest and Isolation Forest). Random seeds were fixed where applicable to ensure consistent and reproducible outputs across runs.

---

## Author

Kenil P Patel
