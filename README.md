# Amazon Basin Hydrological Analysis with GRACE and ERA5 Data

This repository contains a complete workflow for analyzing hydrological data over the Amazon Basin using GRACE (Gravity Recovery and Climate Experiment) and ERA5 datasets. The project involves preprocessing spatiotemporal data, constructing physics-informed neural networks (PINNs), and comparing predicted water storage anomalies (TWSA) with observed GRACE data.

## Table of Contents
1. [Project Description](#project-description)
2. [Requirements](#requirements)
3. [File Descriptions](#file-descriptions)
4. [Workflow Overview](#workflow-overview)
5. [Results](#results)
6. [Acknowledgments](#acknowledgments)

---

## Project Description

The Amazon Basin is a critical region for understanding global hydrological cycles. This project aims to:
- Extract and preprocess GRACE and ERA5 datasets to analyze Total Water Storage Anomalies (TWSA).
- Use machine learning techniques, including Random Forests and Physics-Informed Neural Networks (PINNs), to model and predict TWSA.
- Compare predicted TWSA values with observed GRACE data to evaluate model performance.

The project combines geospatial data processing, time-series analysis, and deep learning to provide insights into hydrological trends in the Amazon Basin.

---

## Requirements

To run this project, you need the following dependencies:

### Python Libraries
- `geopandas`
- `xarray`
- `matplotlib`
- `numpy`
- `pandas`
- `scikit-learn`
- `torch`
- `wandb`

### External Tools
- GRACE Mascon NetCDF files (e.g., `CSR_GRACE_GRACE-FO_RL0602_Mascons_all-corrections.nc`)
- ERA5 hydrological variables (e.g., precipitation, evapotranspiration, runoff)
- Shapefiles for the Amazon Basin (e.g., `hybas_sa_lev03_v1c.shp`)

### Installation
Install the required libraries using `pip`:
```bash
pip install geopandas xarray matplotlib numpy pandas scikit-learn torch wandb
```

---

## File Descriptions

### 1. `making_timeseries.ipynb`
This notebook processes raw GRACE and ERA5 datasets to extract and prepare data for modeling. Key tasks include:
- **Shapefile Filtering**: Extracts the Amazon Basin sub-basins from a global shapefile.
- **GRACE Data Processing**: Loads GRACE mascon data, adjusts time resolution, converts units, and computes spatial averages over the Amazon Basin.
- **Data Interpolation**: Fills missing values in the GRACE dataset using a Random Forest Regressor.
- **ERA5 Data Processing**: Aggregates ERA5 hydrological variables (`tp`, `ro`, `e`) over the Amazon Basin and saves the results.

#### Output Files
- `amazon_basin.shp`: Clipped shapefile for the Amazon Basin.
- `amazone_grace_interpolated_2003_1_2022_12.nc`: Interpolated GRACE data for the Amazon Basin.
- `combined_2003_2022.nc`: Processed ERA5 hydrological variables aggregated over the Amazon Basin.

---

### 2. `torch_timeseries.ipynb`
This notebook implements a Physics-Informed Neural Network (PINN) to model and predict TWSA. Key tasks include:
- **Data Loading**: Loads preprocessed GRACE and ERA5 datasets.
- **Normalization**: Normalizes input variables (precipitation, evapotranspiration, runoff, and TWSA).
- **Cyclic Encoding**: Encodes time as sine and cosine features to capture seasonal patterns.
- **Model Training**: Trains a PINN to predict TWSA while enforcing physical constraints (water balance equation: dTWSA/dt = P - E - RO).
- **Evaluation**: Compares predicted TWSA with observed GRACE data and visualizes results.

#### Output Files
- `pinn_tws_model.pth`: Trained PINN model weights.
- Plots showing the comparison between predicted and true TWSA.

---

## Workflow Overview

1. **Data Preprocessing**:
   - Extract and clip the Amazon Basin from global shapefiles.
   - Process GRACE and ERA5 datasets to compute spatial averages and interpolate missing values.

2. **Modeling**:
   - Normalize and encode input features for the PINN.
   - Train the PINN to predict TWSA while enforcing physical constraints.

3. **Evaluation**:
   - Aggregate daily predictions to monthly scale.
   - Compare predicted TWSA with observed GRACE data.
   - Visualize results to assess model performance.

---

## Results

### PINN Predictions vs. Observed TWSA
The second notebook trains a PINN to predict TWSA and compares the results with observed GRACE data. The model captures seasonal patterns and long-term trends in water storage anomalies.

![PINN Predictions vs. Observed TWSA](https://via.placeholder.com/800x400?text=PINN+Predictions+vs.+Observed+TWSA)

---

## Acknowledgments

- GRACE data provided by the Center for Space Research (CSR) at the University of Texas at Austin.
- ERA5 data provided by the European Centre for Medium-Range Weather Forecasts (ECMWF).
- Shapefiles for the Amazon Basin obtained from the HydroSHEDS database.

---
