# Rainfall Prediction using STL Decomposition, GRU, and LightGBM

## Project Overview
This project focuses on forecasting daily rainfall using a hybrid approach that combines **STL (Seasonal-Trend Decomposition using LOESS)**, **Gated Recurrent Unit (GRU)** networks, and **Light Gradient Boosting Machine (LightGBM)**. The goal is to predict rainfall one day ahead by decomposing the time series into trend, seasonality, and remainder components, modeling each component separately, and combining the predictions for the final output. The study leverages historical weather data from Australia to build and evaluate the models.

## Dataset
The dataset used is available on [Kaggle](https://www.kaggle.com/datasets/parthdande/timeseries-weather-dataset).
The notebook can be seen live on [Kaggle notebook](https://www.kaggle.com/code/patelprerak510/stl-decomposition-gru-lightgbm-rainfall-prediction)
The dataset was preprocessed to handle missing values and resampled for daily predictions.

## Methodology
The project follows a three-step approach:
1. **STL Decomposition**: The rainfall time series is decomposed into **trend**, **seasonality**, and **remainder** components using LOESS (Locally Estimated Scatterplot Smoothing).
2. **Modeling**:
   - **GRU**: A Gated Recurrent Unit network is used to model the **trend** component.
   - **Multi-Time-Scale GRU**: An advanced version of GRU is employed to model the **seasonality** component.
   - **LightGBM**: A gradient boosting framework is used to model the **remainder** component.
3. **Combined Prediction**: The predictions from the three models are aggregated to produce the final rainfall forecast.

## Key Features
- **Exploratory Data Analysis (EDA)**: Analysis of raw data, including histograms, correlation matrices, and time series plots.
- **STL Decomposition**: Separation of time series into trend, seasonality, and remainder components.
- **Deep Learning Models**: GRU and Multi-Time-Scale GRU for capturing temporal dependencies.
- **LightGBM**: Efficient gradient boosting for modeling non-linear relationships.
- **Evaluation Metrics**: R² score, RMSE, and MAE for model performance evaluation.

## Results
The combined model achieved the following performance metrics:
- **R² Score**: 0.7902
- **RMSE**: 3.3351 mm
- **MAE**: 1.3846 mm

The model outperformed the baseline GRU model, which had an R² score of 0.1618, RMSE of 6.6703 mm, and MAE of 2.2121 mm.

### Model Performance Summary
| Model                  | R² Score | RMSE (mm) | MAE (mm) |
|------------------------|----------|-----------|----------|
| GRU (Trend)            | 0.9998   | 0.0077    | 0.0061   |
| Multi-Time-Scale GRU   | 0.9853   | 0.6036    | 0.2895   |
| LightGBM (Remainder)   | 0.6790   | 3.4081    | 1.5664   |
| Combined Model         | 0.7902   | 3.3351    | 1.3846   |
| Baseline GRU           | 0.1618   | 6.6703    | 2.2121   |

## Installation
To run the code, ensure the following dependencies are installed:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn tensorflow lightgbm
