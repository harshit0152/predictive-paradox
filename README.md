# Short-Term Power Demand Forecasting using Machine Learning


---

## Overview

In this project, I developed a machine learning-based time series forecasting system to predict short-term electricity demand. Accurate demand forecasting is essential for efficient power grid management, load balancing, and reducing operational costs.

The model is built using the LightGBM Regressor along with extensive feature engineering techniques to capture temporal patterns and dependencies in the data.

---

## Objectives

* Predict next-hour electricity demand
* Handle time-series data with seasonality
* Improve forecasting accuracy using lag and rolling features
* Evaluate model performance using standard metrics

---

## Dataset Description

The project uses multiple datasets:

* Power Demand Data (PGCB)
* Weather Data (temperature, humidity, etc.)
* Economic Indicators

All datasets are merged based on a common datetime index.

---

## Technology Stack

* Python
* Pandas and NumPy for data processing
* Matplotlib for visualization
* Scikit-learn for evaluation metrics
* LightGBM for model training
* OpenPyXL for Excel file handling

---

## Data Preprocessing

The following preprocessing steps were performed:

* Conversion of datetime column into appropriate format
* Chronological sorting of data
* Removal of duplicate timestamps
* Setting datetime as index
* Handling missing values

---

## Outlier Detection

To improve model robustness:

* Interquartile Range (IQR) was calculated
* A 3 × IQR rule was applied
* Extreme values in demand were identified and filtered

---

## Data Integration

The datasets were merged to create a unified dataset containing:

* Power demand
* Weather variables
* Economic indicators

---

## Feature Engineering

Feature engineering was a critical component of the project.

### Time-Based Features

* Hour of day
* Day of week
* Month
* Day of year
* Week of year

### Lag Features

* 1h, 2h, 3h, 6h, 12h
* 24h, 48h, 72h
* 168h and 336h

### Rolling Statistics

* Rolling mean and standard deviation over:

  * 3h, 6h, 12h
  * 24h, 48h
  * 168h

These features help capture trend, seasonality, and temporal dependencies.

---

## Target Variable

The target variable is defined as the next hour demand:

```python
target = next_hour_demand
```

---

## Train-Test Split

* Training Data: Data before 2024
* Testing Data: Data from 2024

This ensures proper time-series validation without data leakage.

---

## Model

The model used is LightGBM Regressor with the following parameters:

```python
n_estimators = 1500
learning_rate = 0.05
num_leaves = 127
max_depth = 8
subsample = 0.8
colsample_bytree = 0.8
```

LightGBM was selected due to its efficiency and strong performance on tabular datasets.

---

## Evaluation Metrics

The model was evaluated using:

* Mean Absolute Percentage Error (MAPE)
* Mean Absolute Error (MAE)
* Root Mean Squared Error (RMSE)

Predictions were constrained to non-negative values using clipping.

---

## Visualizations

The following visualizations were generated:

* Actual vs Predicted demand
* Feature importance (top features)
* Error distribution (residuals and percentage error)

---

## Results Summary

A summary of results includes:

* Model name
* Test year
* MAPE
* MAE
* RMSE
* Number of features used

---

## Conclusion

This project demonstrates the effectiveness of machine learning techniques for time-series forecasting. Feature engineering played a significant role in improving model performance. LightGBM proved to be a suitable choice for this problem.

---

## Future Work

* Implementation of deep learning models such as LSTM or GRU
* Inclusion of additional external variables such as holidays and events
* Hyperparameter tuning using advanced optimization techniques
* Deployment as a real-time forecasting system

---

## License

This project is licensed under the MIT License.

---

## Acknowledgements

* Dataset providers
* Open-source libraries including LightGBM, Scikit-learn, and Pandas

