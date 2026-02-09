# 🌫️ Next-day PM2.5 Prediction for Delhi (Anand Vihar)

This project studies short-term air-quality forecasting by predicting next-day PM2.5 concentrations at the Anand Vihar monitoring station in Delhi, using recent pollution levels and daily meteorological conditions.

The emphasis is on correct time-series handling and interpretable regression models, rather than complex or black-box approaches.

---

## 🎯 Problem statement

Given daily air-quality and weather information up to day *t*, predict the PM2.5 concentration on day *t + 1*.

---

## 📊 Dataset

Two public datasets are used:

- 🏭 Daily air-quality data containing PM2.5 and other pollutants  
- 🌦️ Hourly weather and air-quality data containing temperature, humidity and wind speed  

The hourly weather data are aggregated to daily averages and merged with the daily air-quality data using the calendar date.  
All modelling is performed at a daily time resolution.

The data correspond to the **Anand Vihar station in Delhi**.

---

## 🧩 Features

The final feature set includes:

- ⏱️ PM2.5 on the current day (`pm25_lag1`)
- 📉 7-day rolling mean of PM2.5 (`pm25_7d_avg`)
- 🌡️ Daily average temperature
- 💧 Daily average humidity
- 🌬️ Daily average wind speed

The target variable is PM2.5 on the next day.

---

## 🤖 Models

The following models are implemented:

- 🟦 Naive persistence baseline  
  *(tomorrow’s PM2.5 = today’s PM2.5)*
- 📐 Linear Regression
- 🌲 Random Forest Regressor

---

## 📐 Evaluation

A proper time-aware split is used:

- ⏳ first 80 % of the time series for training  
- 🧪 last 20 % for testing  

Metrics:

- 📏 Mean Absolute Error (MAE)
- 📐 Root Mean Squared Error (RMSE)

---

## ⭐ Main results

Both regression models achieve noticeably lower MAE and RMSE than the naive persistence baseline, indicating that meteorological variables add predictive value beyond simple day-to-day persistence.

---

## 🔍 Interpretation

- 📐 Linear regression coefficients are used to understand the direction of influence of each variable.
- 🌲 Random forest feature importance is used to assess relative predictive contribution.
- 🔗 The effect of correlation between lagged and rolling PM2.5 features is explicitly discussed.

---

## 📁 Repository contents

The entire analysis is contained in a single, fully reproducible notebook.

---

## ▶️ How to run

Open `pm25_prediction.ipynb` in Kaggle, Jupyter Notebook or Google Colab and run all cells from top to bottom.

Required packages:

- pandas
- numpy
- scikit-learn
- matplotlib
- seaborn
- ipywidgets

---

## ⚠️ Limitations

- 📆 The dataset covers a short time period and a single monitoring station.
- 🌏 Seasonal and long-term patterns cannot be learned reliably.
- 📉 The small sample size limits the stability of estimated feature effects.

---

## 🚀 Next steps

- 🗓️ Extend the analysis to multiple years and additional stations.
- 🚦 Incorporate calendar and traffic-related features.
- 🔄 Perform rolling or expanding-window evaluation to assess temporal stability.

---

👩‍🎓 **Author:** Mayank Kochar
