# Psychosocial Predictors of Suicide Attempt in Adolescents with a History of Self-Harm: A Machine Learning Study with Actigraphy

This repository contains the analysis code for a study examining whether actigraphy-derived arousal markers and questionnaire-based psychosocial measures collected at age 14 predict self-reported suicide attempts at age 17, in a population-based sample of adolescents with a history of self-harm from the UK Millennium Cohort Study (MCS).

The study used univariable and multivariable logistic regression, nested-cross-validation machine learning (XGBoost, MLP, logistic regression), SHAP-based feature importance, and a two-stage classification framework (questionnaire-only, then + actigraphy for individuals classified as low-risk in stage one).

## Data availability

This project uses data from the **Millennium Cohort Study**, a restricted-access UK birth cohort study distributed via the UK Data Service / CLOSER. Individual-level participant data, including raw and preprocessed CSV files referenced by these notebooks (e.g. `mcs_sh_sample_Feb_28.csv` and similar), **are not included in this repository** and cannot be shared publicly under the data access agreement.

Researchers wishing to reproduce these analyses can apply for access to the Millennium Cohort Study through the UK Data Service (https://ukdataservice.ac.uk) or CLOSER (https://closer.ac.uk).

For the same reason, per-participant model predictions (fold-level prediction files) are also excluded. Only aggregate/summary results (fold-level performance metrics, overall summaries, descriptive statistics, odds ratios, and SHAP visualizations) are included in `results/`.

## Repository structure

```
notebooks/                  Analysis notebooks (see below)
preprocessing_files/        Binning metadata and feature-dropping metadata used in preprocessing
results/
  descriptive/               Descriptive statistics and missingness tables
  or/                         Univariable/multivariable logistic regression (odds ratio) results
  ml/                         Nested-CV model performance, top features, SHAP summary plots
  two_stage/                  Two-stage classification summary and fold-level metrics (aggregate only)
requirements.txt
LICENSE
```

## Notebooks

| Notebook | Purpose |
|---|---|
| `2_Preprocessing.ipynb` | Data cleaning, feature binning, and preprocessing of the raw MCS extract |
| `Descriptive_table.ipynb` | Descriptive statistics and missingness summaries |
| `missingness_analysis.ipynb` | Detailed missing-data analysis |
| `OR_analyses.ipynb` | Univariable and multivariable logistic regression (odds ratios) |
| `Forest_plot_univariate.ipynb` | Forest plot of univariable odds ratios |
| `Forest_plot_multivariable.ipynb` | Forest plot of multivariable odds ratios |
| `3_Analyses.ipynb` | Main nested cross-validation machine learning pipeline (XGBoost, MLP, logistic regression), SHAP analysis |
| `actig_only_sample.ipynb` | Preparation of the actigraphy subsample |
| `Analyses_two_step.ipynb` | Two-stage classification (questionnaire-only, then + actigraphy) |

Note: file paths inside these notebooks have been changed to relative placeholders (e.g. `../data/...`) since the underlying MCS data files cannot be redistributed. The notebooks are shared for methodological transparency and are not intended to run end-to-end without independently obtained access to the Millennium Cohort Study data.

## Requirements

See `requirements.txt`. Python 3.9+ recommended.

```bash
pip install -r requirements.txt
```

## Citation

If you use this code, please cite the associated manuscript (citation to be added upon publication).

## License

Code is released under the MIT License (see `LICENSE`). This license applies to the analysis code only, not to the Millennium Cohort Study data, which remains subject to its own access and use terms.
