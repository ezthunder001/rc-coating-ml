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

## Data (Demo)
Placeholder 24-hour outdoor surface temperature measurements (1-minute intervals) across
19 formulation IDs and 1 bare reference. Same structure as the production dataset.
Key target: daytime peak DeltaT vs bare substrate.

## Pipeline
1. **EDA** - distributions, cooling profiles, day/night separation, correlations
2. **Feature engineering** - extract daytime peak DeltaT, mean DeltaT, time-of-peak per sample
3. **Model** - Random Forest regressor mapping formulation parameters to cooling performance
4. **Interpretation** - feature importance to guide next experiment design

## Project Structure
```
rc-coating-ml/
├── data/raw/           # demo CSVs (same structure as production data)
├── notebooks/          # EDA and modelling notebooks
├── figures/            # generated plots (gitignored)
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
- [ ] Feature engineering notebook
- [ ] Random Forest baseline model
- [ ] Cross-validation + error analysis
- [ ] Full dataset integration (post-publication)
