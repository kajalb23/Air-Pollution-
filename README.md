# Air Pollution Forecasting Using Multivariate Time Series

## Objective

The objective of this project is to forecast PM2.5 air pollution levels using multivariate time series data. The model aims to learn temporal patterns from various environmental factors and predict the concentration of particulate matter (PM2.5) for future time steps. This can aid in proactive environmental monitoring and decision-making.

---

## Dataset

- **Name:** Beijing PM2.5 Dataset  
- **Source:** UCI Machine Learning Repository  
- **Type:** Multivariate Time Series  
- **Size:** Approximately 43,800 rows (hourly data from 2010 to 2014)  
- **Format:** CSV  
- **Target Variable:** `pollution` (PM2.5 concentration in µg/m³)

### Features

| Column Name | Description                   | Type        |
|-------------|-------------------------------|-------------|
| pollution   | PM2.5 concentration (target)  | Continuous  |
| dew         | Dew point temperature         | Continuous  |
| temp        | Ambient temperature           | Continuous  |
| pres        | Atmospheric pressure          | Continuous  |
| wnd_dir     | Wind direction                | Categorical |
| wnd_spd     | Cumulative wind speed         | Continuous  |
| snow        | Hours of snow                 | Continuous  |
| rain        | Hours of rain                 | Continuous  |
| date        | Timestamp                     | Datetime    |

---

## Workflow :

### 1. Data Preprocessing

- Parsed the `date` column to create a datetime index.
- Handled missing values by replacing them or dropping affected rows.
- Dropped the first 24 hours due to incomplete data.
- Encoded categorical variable `wnd_dir` using `LabelEncoder`.
- Applied `MinMaxScaler` to normalize features to the range [0, 1].
- Transformed the time series into a supervised learning format using sliding windows of 4 past time steps.

### 2. Model Development

- Used an LSTM (Long Short-Term Memory) neural network to capture temporal dependencies in the data.
- Constructed a 3-layer stacked LSTM model with dropout regularization.
- Used `mean_squared_error` as the loss function and `adam` as the optimizer.
- Trained the model for 20 epochs with a batch size of 32.

### 3. Model Evaluation

- Split the dataset chronologically into training and testing sets.
- Evaluated performance using standard regression metrics: MAE, MSE, RMSE, and R² score.
- Compared predicted PM2.5 values to actual values to assess forecast accuracy.

---

## Evaluation Summary

| Metric                   | Value               |
|--------------------------|---------------------|
| Mean Squared Error (MSE) | 846.47              |
| Root Mean Squared Error (RMSE) | 29.09        |
| R² Score                 | 0.90                |
| Mean of Test Data        | 95.81 µg/m³         |


---

