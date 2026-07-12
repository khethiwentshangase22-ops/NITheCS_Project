# Evaluating Conformal Prediction for Temperature Forecasting in Cape Town

This repository contains the Python/Jupyter Notebook used for the research project:

**Evaluating Conformal Prediction for Uncertainty Quantification in Machine Learning-Based Temperature Prediction: A Case Study of Cape Town, South Africa**

## Project Overview

This project evaluates whether conformal prediction can provide useful uncertainty estimates for machine learning-based next-day maximum temperature forecasting in Cape Town, South Africa.

The main idea is that ordinary machine learning models usually provide only point predictions, such as a single predicted temperature value. Conformal prediction is used to add prediction intervals around those forecasts, helping to show how reliable or uncertain each prediction is.

## Research Focus

The project focuses on:

- next-day maximum temperature forecasting;
- comparing different machine learning models;
- applying split conformal prediction for uncertainty quantification;
- evaluating the trade-off between coverage and prediction interval width;
- testing confidence levels of 80%, 90%, and 95%.

## Data Source

Historical daily weather data is obtained from the **Open-Meteo Historical Weather API** for Cape Town, South Africa.

The main variables used are:

- daily maximum temperature (TMAX);
- daily minimum temperature (TMIN);
- daily mean temperature (TMEAN);
- daily precipitation (PRCP);
- lagged temperature variables;
- cyclical time features for month and day of year.

## Models Used

The following machine learning models are evaluated:

1. **Random Forest**
2. **XGBoost**
3. **Multilayer Perceptron (MLP)**

These models are selected because they represent different modelling approaches. Random Forest and XGBoost are tree-based models, while MLP provides a neural network approach.

## Main Workflow

The notebook follows this workflow:

1. Import required Python libraries.
2. Load Cape Town historical weather data from Open-Meteo.
3. Rename variables for readability.
4. Perform exploratory data analysis.
5. Create the next-day target variable (`TMAX_next`).
6. Create lagged temperature variables.
7. Apply cyclical encoding to seasonal time features.
8. Split the data chronologically into training, calibration, and test sets.
9. Train Random Forest, XGBoost, and MLP models.
10. Tune model hyperparameters using GridSearchCV and TimeSeriesSplit.
11. Apply split conformal prediction using MAPIE.
12. Evaluate predictive performance using MAE, RMSE, and R².
13. Evaluate uncertainty performance using coverage and average interval width.
14. Test conformal confidence levels of 80%, 90%, and 95%.
15. Save prediction results and output tables.

## Evaluation Metrics

Predictive performance is evaluated using:

- Mean Absolute Error (MAE);
- Root Mean Squared Error (RMSE);
- Coefficient of Determination (R²).

Uncertainty performance is evaluated using:

- empirical coverage;
- average prediction interval width.

## Key Findings

The tuned MLP model performs best among the individual models, achieving the strongest overall predictive performance and relatively narrow conformal prediction intervals.

The conformal prediction results show the expected trade-off:

- lower confidence levels give narrower intervals but lower coverage;
- higher confidence levels give higher coverage but wider intervals;
- the 90% confidence level provides a practical balance between reliability and interval width.

## Main Python Libraries

The project uses the following Python libraries:

- `pandas`
- `numpy`
- `requests`
- `matplotlib`
- `seaborn`
- `scikit-learn`
- `xgboost`
- `mapie`
- `statsmodels`

## Repository Contents

```text
Temperature_Prediction.ipynb
README.md
processed_temperature_data.csv
hyperparameter_tuning_results.csv
tuned_conformal_results.csv
predictions_with_uncertainty_80_90_95.csv
model_comparison_resuls
```

## Author

**Khethiwe Ntshangase**

## Project Context

This project is completed as part of the NITheCS research project work for the Winter Internship Programme.

## AI Declaration

Microsoft Copilot was used as a support tool to help clarify concepts, improve wording, structure explanations, and assist with code organisation. All results, interpretations, and final decisions were reviewed and verified by the author. The final work reflects the author's own understanding and responsibility.
