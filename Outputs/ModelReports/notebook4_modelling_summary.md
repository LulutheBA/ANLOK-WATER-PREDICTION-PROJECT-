# ANLOK Water Prediction Project — Notebook 4 Modelling Report

## 1. Dataset
Outputs/FeatureEngineering/NIWIS_Water_Supply_Reliability_-_population_16-Jul-2026__engineered.csv

## 2. Target variable
`target_reliable_supply_pct`, derived from `population_reliable_supply_1`.

This is a water-service reliability target. It is used as an outage-risk proxy:
**outage-risk proxy = 100 - predicted reliable-supply percentage**.

The current project does not contain a verified event-level historical outage target, so this notebook does not claim direct outage-event prediction.

## 3. Observations
144

## 4. Features before feature engineering
12

## 5. Features after feature engineering
12

## 6. Train / validation / test
- Train: 100
- Validation: 22
- Final test: 22

## 7. Models tested
- Dummy Baseline
- Ridge Regression
- Random Forest
- Gradient Boosting
- HistGradientBoosting
- Extra Trees

## 8. Best model
Extra Trees

## 9. Best validation performance
- Validation RMSE: 12.9126

## 10. Final test performance
- MAE: 7.8563
- RMSE: 10.3178
- R²: 0.5536
- MAPE: 11.76%

## 11. Most important features
- water_access_rate_pct
- water_access_gap_pct
- rural_population_share_pct
- urban_population_share_pct
- rural_population
- rural_population_with_access_to_water
- population
- wsa_name
- population_with_access_to_water
- urban_population

## 12. Geographic experiment
Geographic features improved validation RMSE: True

## 13. Weather decision
Weather was not included in the primary model because the project does not provide a validated municipality-date key connecting daily weather observations to the cross-sectional reliability target.

## 14. Limitations
- No verified historical outage-event target.
- Reliability is a proxy rather than direct outage prediction.
- The selected target is cross-sectional rather than an event-level time series.
- Daily weather cannot be safely assigned to target observations without a municipality-date join.
- Small municipal samples limit claims about operational deployment.
- Predictions should be treated as decision-support estimates, not outage alarms.

## 15. Data needed for a true outage prediction system
- Historical outage/service-interruption events.
- Municipality or water-service-area identifier for every event.
- Outage start and end timestamps or duration.
- Outage cause/type.
- Pump, reservoir, treatment and infrastructure failure records.
- Maintenance records.
- Reservoir level/capacity observations where available.
- A consistent municipality-date key for joining weather.
- Water demand/consumption observations aligned to the same dates.

## 16. Notebook 5 recommendations
- Present the model comparison and cross-validation evidence.
- Present the untouched final-test metrics.
- Present Gauteng municipality risk-proxy predictions.
- Explain why reliability is a proxy rather than direct outage prediction.
- Present feature importance and the geographic experiment.
- Link model findings directly to Gauteng water-service challenges.
- Clearly document the data required for future direct outage prediction.

Gauteng municipality predictions were generated and saved.
