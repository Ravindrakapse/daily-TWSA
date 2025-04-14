# Daily TWSA (Total Water Storage Anomaly) Analysis

This repository contains code and notebooks for analyzing daily Total Water Storage Anomaly (TWSA) data. The project focuses on processing and analyzing time series data related to water storage variations using PyTorch and other data science tools.

## Project Overview

The project includes tools and notebooks for:
- Processing and analyzing GRACE satellite data for water storage anomalies
- Time series analysis using PyTorch
- Data visualization and preprocessing techniques

## Repository Structure

```
daily TWSA/
├── torch_timeseries.ipynb     # PyTorch-based time series analysis
├── making_timeseries.ipynb    # Data preparation and time series creation
└── README.md                  # Project documentation
```

## Requirements

The project requires the following main dependencies:
- Python 3.x
- PyTorch
- Jupyter Notebook
- NumPy
- Pandas
- Matplotlib

## Usage

1. Clone this repository
2. Install the required dependencies
3. Open the Jupyter notebooks to:
   - Process time series data using `making_timeseries.ipynb`
   - Analyze the data using PyTorch with `torch_timeseries.ipynb`

## Notebooks Description

### making_timeseries.ipynb
- Data preparation and preprocessing
- Time series creation from raw data
- Initial data visualization and analysis

### torch_timeseries.ipynb
- PyTorch-based time series analysis
- Model implementation and training
- Results visualization and evaluation

## Data Sources

The project uses GRACE satellite data for analyzing Total Water Storage Anomalies. The data processing includes:
- GRACE satellite measurements
- Time series interpolation
- Anomaly calculations

## Contributing

Feel free to fork this repository and submit pull requests. For major changes, please open an issue first to discuss what you would like to change.

## License

[MIT License](https://choosealicense.com/licenses/mit/) 