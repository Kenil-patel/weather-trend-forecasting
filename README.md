# Weather Trend Forecasting Project

## Overview

This project analyzes global daily weather data and forecasts future temperature trends using time‑series modeling and machine learning techniques. The goal is to demonstrate a complete data science workflow including preprocessing, exploratory analysis, forecasting, anomaly detection, and feature importance interpretation.

---

## Dataset

**Global Weather Repository (Kaggle)**
Contains worldwide daily weather measurements across multiple cities and countries including temperature, precipitation, humidity, and pressure.

Target variable: **temperature_celsius**
Time column: **last_updated**

---

## Project Pipeline

### 1. Data Cleaning & Preprocessing

* Converted `last_updated` to datetime and set as index
* Sorted chronologically for time‑series analysis
* Handled missing values using forward/backward fill
* Removed outliers using IQR method (temperature in Celsius only)
* Standardized numeric features using StandardScaler

### 2. Exploratory Data Analysis (EDA)

Performed visualization and statistical analysis:

* Temperature trend over time
* Precipitation trend
* Correlation heatmap (numeric features only)
* Monthly seasonal patterns

Key Insight:
The dataset exhibits seasonal periodicity, making it suitable for seasonal time‑series forecasting models.

---

### 3. Forecasting Models

Two forecasting models were implemented and compared:

#### SARIMA

Captures trend and seasonality using autoregressive structure.

Metrics:

* MAE
* RMSE

#### Prophet

Captures long‑term seasonal patterns and trend decomposition.

Metrics:

* MAE
* RMSE

Model comparison performed to determine best forecasting performance.

---

### 4. Advanced Analysis

#### Anomaly Detection

Isolation Forest used to detect unusual weather conditions (e.g., extreme temperature events).

#### Feature Importance

Random Forest regression used to identify meteorological variables influencing temperature variation.

#### Climate Analysis

Country‑level temperature variability analyzed using standard deviation to observe regional climate stability differences.

---

## Results Summary

* SARIMA handled short‑term fluctuations effectively
* Prophet captured long seasonal patterns better
* Humidity and pressure were strong predictors of temperature
* Detected anomalies correspond to extreme weather events
* Coastal regions showed lower temperature variability than inland regions

---
## Practical Applications
- Energy demand planning
- Agriculture risk prediction
- Climate monitoring
- Smart city weather adaptation
- Event planning and logistics
  
---

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib & Seaborn
* Scikit‑learn
* Statsmodels (SARIMA)
* Prophet

---

## How to Run

1. Install dependencies

```
pip install pandas numpy matplotlib seaborn scikit-learn statsmodels prophet
```

2. Place dataset inside project folder

```
data/GlobalWeatherRepository.csv
```

3. Run notebook cells in order

* Data Cleaning
* EDA
* Forecasting
* Advanced Analysis

---

## Project Structure

```
weather-forecasting-project/
│── data/
│── notebooks/
│── images/
│── README.md
```

---

## PM Accelerator Mission

(Add official mission statement from PM Accelerator website here in the final submission presentation/report.)

---

## Reproducibility
Results may slightly vary due to stochastic models (Random Forest, Isolation Forest).
Random seeds were fixed where applicable.



## Author

Kenil P Patel

