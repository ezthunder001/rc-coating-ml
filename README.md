# rc-coating-ml

Predicting sub-ambient cooling performance of passive surface coatings from formulation
parameters using machine learning.

> **Note:** The dataset in this repository is placeholder/demo data that mirrors the
> structure of the real experimental dataset. The full research data will be released
> alongside publication. This repo demonstrates the ML pipeline architecture.

## Problem
Selecting the optimal filler composition for a passive cooling coating currently requires
iterative 24-hour outdoor experiments, and each run tests only a small number of variants.
This project builds an ML pipeline to predict sub-ambient surface temperature (DeltaT vs
reference) from formulation parameters, reducing the number of experiments needed.

## Pipeline

```
Raw CSV  ->  EDA  ->  Feature Engineering  ->  Random Forest  ->  Experiment Recommendations
  01           01              02                    03
```

## Results (Demo Data)

| Metric | Value |
|--------|-------|
| CV Strategy | Leave-One-Out (n=19) |
| R2 | 0.911 |
| MAE | 0.075 degC |
| RMSE | 0.107 degC |
| Top feature | mean_dT_day |

## Notebooks

| Notebook | Description |
|----------|-------------|
| `01_eda_rc_coating.ipynb` | EDA: distributions, 24h profiles, correlations |
| `02_features.ipynb` | Feature engineering from time-series + formulation metadata |
| `03_model.ipynb` | Random Forest + LOOCV + feature importance + error analysis |

## Project Structure
```
rc-coating-ml/
├── data/
│   ├── raw/            # demo temperature CSVs (same structure as production)
│   └── features.csv    # extracted feature matrix
├── notebooks/          # EDA, features, model
├── figures/            # generated plots (gitignored)
└── requirements.txt
```

## Quick Start
```bash
python -m venv .venv && .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook
```
Run notebooks in order: 01 -> 02 -> 03.

## Status
- [x] Environment setup
- [x] EDA notebook (01_eda_rc_coating.ipynb)
- [x] Feature engineering (02_features.ipynb)
- [x] Random Forest + LOOCV (03_model.ipynb)
- [ ] Full dataset integration (post-publication)
