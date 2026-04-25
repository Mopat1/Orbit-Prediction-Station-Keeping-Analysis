# Orbit Prediction & Station-Keeping Analysis

A machine learning based aerospace analytics project for predicting geostationary satellite orbital drift, evaluating station-keeping requirements, and generating operational insights using propagated orbital data.

---

## Overview

This project builds an end-to-end pipeline for:

* Satellite orbit propagation from TLE data
* Orbital feature engineering
* Inclination drift prediction
* Altitude deviation forecasting
* Cross-validation of prediction models
* Residual error diagnostics
* Station-keeping delta-V estimation
* Time-series forecasting of future orbital behaviour

The system is designed around **GEO satellites**, where maintaining orbital slot accuracy is critical for communication and weather missions.

---

## Motivation

Geostationary satellites experience gradual orbital drift due to:

* Earth's oblateness (J2 perturbation)
* Lunar and solar gravity
* Solar radiation pressure
* Small long-term disturbances

These effects require periodic **North-South** and **East-West station-keeping manoeuvres**.

This project explores whether machine learning can forecast drift patterns early and support fuel-efficient orbital maintenance planning.

---

## Features

### Orbit Data Pipeline

* TLE ingestion
* SGP4 propagation (or simulated fallback mode)
* Multi-satellite dataset generation
* Time-indexed orbital state vectors

### Feature Engineering

Generated features include:

* Inclination
* Altitude
* Radius magnitude
* Velocity magnitude
* Orbital energy
* Lag features
* Rolling mean / rolling std
* Time cyclic encodings
* Drift deltas

### Machine Learning Models

* Gradient Boosting Regressor
* Random Forest Regressor
* Ridge Regression
* Linear Regression

### Validation

* Train/Test evaluation
* Walk-forward time-series cross validation
* Residual diagnostics
* Forecast error metrics

### Operational Outputs

* Predicted inclination drift
* Predicted altitude deviation
* Station-keeping manoeuvre flags
* Delta-V budget estimation

---

## Example Results

| Metric           | Best Value |
| ---------------- | ---------- |
| Inclination MAE  | 0.000119°  |
| Inclination RMSE | 0.000135°  |
| Altitude MAE     | 0.0151 km  |
| Forecast MAE     | 0.000001°  |

---

## Supported Satellites

Example GEO satellites used:

* INSAT-3D
* GSAT-17
* GSAT-11
* SES-12
* MEASAT-3B

---

## Project Structure

```text
orbit_pipeline.py        # Orbit generation + feature engineering
model.py                 # ML models + forecasting utilities
evaluation.py            # Validation + reporting
orbit_dataset.csv        # Generated dataset
eval_metrics.csv         # Model metrics
station_keeping_budget.csv
summary.json
```

---

## Installation

```bash
pip install numpy pandas scikit-learn
pip install sgp4
```

Optional:

```bash
pip install matplotlib seaborn
```

---

## Usage

### Step 1: Generate Dataset

```bash
python orbit_pipeline.py
```

### Step 2: Train Models

```bash
python model.py
```

### Step 3: Full Evaluation

```bash
python evaluation.py
```

---

## Output Files

### orbit_dataset.csv

Contains propagated satellite states and engineered features.

### eval_metrics.csv

Contains:

* MAE
* RMSE
* Per satellite performance

### station_keeping_budget.csv

Contains:

* Mean inclination
* Max inclination
* Estimated delta-V
* Annual station-keeping budget

---

## Engineering Concepts Used

* Orbital Mechanics
* Keplerian Motion
* GEO Station-Keeping
* Supervised Learning
* Time-Series Forecasting
* Feature Engineering
* Residual Analysis

---

## Future Improvements

* Real historical TLE ingestion from public sources
* Live satellite drift dashboard
* XGBoost / LightGBM integration
* Maneuver anomaly detection
* Fuel depletion modelling
* Reinforcement learning for autonomous station-keeping

---

## Applications

* Space operations analytics
* Satellite fleet monitoring
* Aerospace AI research
* Mission planning support
* Academic orbital mechanics projects

---

## Sample Resume Bullet

Developed a machine learning pipeline for geostationary satellite orbit drift prediction and station-keeping analysis using propagated orbital telemetry, achieving sub-milliradian forecasting accuracy across multiple satellites.

---

## Author

Orbit Analysis Project

---

## License

MIT License
