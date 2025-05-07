# IoT Pollution Prediction with Bagging Regressor

This project aims to predict air pollution indicators (NO, NO2, O3, PM10) using a Bagging Regressor ensemble model wrapped in a MultiOutputRegressor. It uses meteorological and pollution data collected from IoT sensors, including features like CO, NOx, O3, PM10, SO2, temperature, pressure, and more.

## Project Structure

```
iot_bagging_regressor_project/
├── data/
│   ├── day.xls                # Daily aggregated pollution and weather data
│   └── hour.xls               # Hourly pollution and weather data
├── notebooks/
│   └── main_analysis.ipynb    # Main Jupyter notebook with full analysis
├── results/
│   ├── plots/                 # Prediction vs actual plots for each target
│   ├── model_metrics.txt      # Saved evaluation metrics (R^2, MAE)
│   └── best_bagging_model.pkl # Serialized trained model (joblib)
├── requirements.txt           # Dependencies
└── README.md                  # This file
```

## Workflow Summary

1. **Setup** : Python environment created using `venv`, required libraries listed in `requirements.txt`
2. **Data Loading** : `day.xls` and `hour.xls` loaded and merged on the date column
3. **Data Preprocessing** :

* Nulls handled
* Features selected: `CO`, `NO`, `NO2`, `NOx`, `O3`, `PM10`, `SO2`, `hour_of_day`, `weekday`
* Targets: `NO`, `NO2`, `O3`, `PM10`
* Train/test split using `train_test_split`
* Feature scaling using `RobustScaler`

1. **Model Training** :

* Used `BaggingRegressor` wrapped in `MultiOutputRegressor`
* Hyperparameter tuning using `GridSearchCV` with cross-validation
* Best model selected and evaluated

1. **Evaluation** :

* `R^2 Score`: ~0.81
* `MAE`: ~12.11
* Plots generated for actual vs predicted values

1. **Outputs** :

* Model performance metrics
* Prediction plots
* Trained model serialized

## How to Use

1. Clone the repository
2. Create a virtual environment and install dependencies:
   ```bash
   python -m venv venv
   source venv/bin/activate  # or venv\Scripts\activate on Windows
   pip install -r requirements.txt
   ```
3. Run `main_analysis.ipynb` in Jupyter
4. Check results in the `results/` folder

## Dependencies

See `requirements.txt` for the full list.

## Author

Andrej Anastasovski
