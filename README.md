# rc-coating-ml

Predicting sub-ambient cooling performance of passive surface coatings from formulation
parameters using machine learning.

## Problem
Selecting the optimal filler composition for a passive cooling coating currently requires
iterative 24-hour outdoor experiments, and each run tests only a small number of variants.
This project trains a regression model on existing measurement data to predict sub-ambient
surface temperature (DeltaT vs reference) from formulation parameters, accelerating the
design cycle.

## Data
24-hour outdoor surface temperature measurements (1-minute intervals) across 19 coating
formulations and 1 bare reference, collected under real outdoor conditions in a hot-humid
tropical climate. Key target: daytime peak DeltaT vs bare substrate.

## Approach
1. **EDA** - distribution, correlations, day/night performance profiles
2. **Feature engineering** - extract daytime peak DeltaT, mean DeltaT, time-of-peak per sample
3. **Model** - Random Forest regressor to map formulation parameters to cooling performance
4. **Iteration** - cross-validation, error analysis, connect back to next experiment design

## Project Structure
```
rc-coating-ml/
├── data/raw/           # outdoor temperature CSVs (anonymized, immutable)
├── notebooks/          # EDA and modelling notebooks
├── figures/            # generated plots
└── requirements.txt
```

## Quick Start
```bash
python -m venv .venv && .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook notebooks/01_eda_rc_coating.ipynb
```

## Status
- [x] Environment setup
- [x] EDA notebook (01_eda_rc_coating.ipynb)
- [ ] Feature engineering
- [ ] Random Forest model
- [ ] Cross-validation + error analysis
