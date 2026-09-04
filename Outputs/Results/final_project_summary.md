# ANLOK WATER PREDICTION PROJECT

## Problem
The project investigates water-service reliability in South African municipal/service areas using publicly available data and machine-learning methods.

## Dataset
Notebook 4's final modelling table contains 144 observations and 12 predictors.

## Methodology
Notebook 4 used a train/validation/final-test design. Models were selected on validation performance and the selected final model was evaluated once on the held-out test set.

## Data Preparation
Notebook 5 reuses the exact Notebook 4 modelling table and the saved fitted model pipeline. It does not repeat data cleaning or silently drop rows.

## Feature Engineering
The final predictor set includes population, water-access, urban/rural composition and the municipality/service-area identifier used by Notebook 4.

## Models Evaluated
- Ridge Regression
- Extra Trees
- Gradient Boosting
- Random Forest
- HistGradientBoosting
- Dummy Baseline

## Final Model
Extra Trees

## Evaluation Results
- MAE: 7.8563
- MSE: 106.4573
- RMSE: 10.3178
- R²: 0.5536
- MAPE: 11.76%
- Final test observations: 22

## Important Features
- water_access_rate_pct
- water_access_gap_pct
- rural_population_share_pct
- urban_population_share_pct
- rural_population

## Key Findings
The selected Extra Trees model achieved moderate held-out explanatory performance. Its average absolute error was 7.86 reliability percentage points.
The most influential predictors indicate that measured water access and urban/rural population structure carry important predictive information for the reliability target.

## Error Analysis
The largest absolute error in the held-out test set was 31.16 percentage points for Mohokare. The mean residual was 1.80 percentage points.

## Limitations
- The project does not contain a verified historical event-level water-outage target. The model predicts water-service reliability instead.
- The outage-risk value is a complement of predicted reliability, not a calibrated probability of an outage.
- The modelling dataset contains 144 municipal/service-area observations, which is small for broad operational deployment.
- The target is cross-sectional rather than an event-level time series, so the model cannot learn outage timing or duration.
- Daily weather was not joined to the primary reliability model because the project lacks a validated municipality-date key connecting those observations.
- Model predictions reflect associations present in the available data and should not be interpreted as causal effects.
- External validation on new municipalities and newer reporting periods is still required before operational use.

## Scalability
The current pipeline is reproducible and can support additional municipal observations, but operational scaling requires more historical data, aligned temporal keys, infrastructure data, external validation and model monitoring.

## Recommendations
### Technical recommendations
- Collect verified historical outage/service-interruption events.
- Add outage start/end timestamps, duration, cause and affected area.
- Create a consistent municipality-date key for safe weather joins.
- Add infrastructure condition, pump, treatment and reservoir data.
- Add aligned water-demand and consumption observations.
- Collect more municipalities and multiple reporting periods.
- Perform external validation on unseen regions and newer time periods.
- Monitor model drift and error if the model is later deployed.

### Problem-domain recommendations
- Use predictions to prioritise areas for investigation, not as automatic outage declarations.
- Combine model outputs with engineering inspections and operational water-system data.
- Treat large residuals as signals for data-quality review or missing local explanatory variables.

## Conclusion
The ANLOK project demonstrates an end-to-end data-science workflow from public water data through cleaning, exploratory analysis, feature engineering, machine-learning modelling, validation and final interpretation. The final model predicts water-service reliability and can support prioritisation of areas for further investigation. It must not be presented as a verified outage-event forecasting system.
