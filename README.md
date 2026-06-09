# nutrition-chd-srilanka

This repository contains the analysis code, de-identified analytic data files, result tables, and figures for the manuscript:

**On the Impact of Fruit and Vegetable Consumption on Coronary Heart Disease Risk Factors: A Case Study from Sri Lanka**

The study examines how total fruit and vegetable intake relates to dietary nutrient profiles and cardiometabolic risk markers in a cross-sectional sample of Sri Lankan adults. The analysis combines exploratory data analysis, Spearman correlation analysis, energy-adjusted nutrient analyses, between-strata heterogeneity testing, regression-based sensitivity checks, female-only sensitivity analysis, and supervised regression modelling.

## Repository contents

The repository currently contains the following main files.

### Analysis notebook

* `chd-srilanka_analysis.ipynb`
  Main Jupyter notebook used for data preprocessing, exploratory analysis, correlation analysis, energy-adjusted nutrient analysis, regression-based sensitivity checks, and machine-learning model benchmarking.

### Data files

* `heart_new.xlsx`
  Main de-identified dataset used for the updated analysis.

* `heart_filtered.csv`
  Filtered analytic dataset after applying the main inclusion criterion for observed fasting insulin values.

* `heart_leq200.csv`
  Analytic subset with total fruit and vegetable intake `<= 200 g/day`.

* `heart_g200.csv`
  Analytic subset with total fruit and vegetable intake `> 200 g/day`.

### Result tables

* `le200_energy_adjusted_density_corr.csv`
  Energy-adjusted nutrient-density correlations in the `<= 200 g/day` stratum.

* `le200_energy_adjusted_residual_corr.csv`
  Energy-adjusted residual-method correlations in the `<= 200 g/day` stratum.

* `g200_energy_adjusted_density_corr.csv`
  Energy-adjusted nutrient-density correlations in the `> 200 g/day` stratum.

* `g200_energy_adjusted_residual_corr.csv`
  Energy-adjusted residual-method correlations in the `> 200 g/day` stratum.

* `heterogeneity_le200_vs_gt200.csv`
  Between-strata heterogeneity tests comparing Spearman correlations in the `<= 200 g/day` and `> 200 g/day` strata.

* `linear_reg_total_quantity_confounding_checks.csv`
  Regression-based sensitivity analyses assessing whether associations between total fruit and vegetable intake and selected cardiometabolic endpoints are attenuated after adjustment for age, sex, and total energy intake.

* `model_evaluation_results_fullsample.csv`
  Machine-learning model evaluation results in the full insulin-observed analytic sample.

* `model_evaluation_results.csv`
  Machine-learning model evaluation results for subgroup or sensitivity analyses.

### Figure files

* `violin_total_by_strata.pdf`
  Distribution of fruit, vegetable, and total fruit and vegetable intake by intake stratum.

* `raincloud_leq200.pdf`
  Raincloud plots for variables in the `<= 200 g/day` stratum.

* `raincloud_g200.pdf`
  Raincloud plots for variables in the `> 200 g/day` stratum.

* `scatter_total_quantity_vs_targets_leq200.pdf`
  Scatterplots of total fruit and vegetable intake against selected cardiometabolic endpoints in the `<= 200 g/day` stratum.

* `scatter_total_quantity_vs_targets_g200.pdf`
  Scatterplots of total fruit and vegetable intake against selected cardiometabolic endpoints in the `> 200 g/day` stratum.

* `spearman_corr_total_quantity_fullsample.pdf`
  Spearman correlations between total fruit and vegetable intake and study variables in the full analytic sample.

* `spearman_corr_total_quantity_leq200.pdf`
  Spearman correlations in the `<= 200 g/day` stratum.

* `spearman_corr_total_quantity_g200.pdf`
  Spearman correlations in the `> 200 g/day` stratum.

* `r2_by_target_model_fullsample.pdf`
  Held-out test `R^2` by target and model in the full analytic sample.

* `rmse_by_target_model_fullsample.pdf`
  Held-out test RMSE by target and model in the full analytic sample.

* `r2_by_target_model_g200.pdf`
  Held-out test `R^2` by target and model in the `> 200 g/day` subgroup.

* `rmse_by_target_model_g200.pdf`
  Held-out test RMSE by target and model in the `> 200 g/day` subgroup.

## Analysis overview

The main analysis follows these steps:

1. Load the updated de-identified dataset.
2. Apply preprocessing, type conversion, range checks, and derived-variable verification.
3. Restrict the main analytic sample to participants with observed fasting insulin values.
4. Define total fruit and vegetable intake in grams per day as the primary dietary exposure.
5. Stratify the sample into:

   * `<= 200 g/day`
   * `> 200 g/day`
6. Summarize participant characteristics and intake distributions.
7. Estimate Spearman correlations between total fruit and vegetable intake and study variables.
8. Perform energy-adjusted nutrient analyses using:

   * nutrient-density method
   * residual method
9. Test between-strata heterogeneity in correlations.
10. Perform regression-based sensitivity analyses adjusted for age, sex, and total energy intake.
11. Conduct a female-only sensitivity analysis.
12. Benchmark supervised regression models for selected cardiometabolic and dietary endpoints.

## Machine-learning models

The supervised regression benchmark includes:

* Lasso
* Ridge
* Bayesian Ridge
* Random Forest
* Support Vector Regression with a linear kernel
* XGBoost

Model performance is evaluated using held-out test `R^2` and RMSE. RMSE should be interpreted within each endpoint because outcomes are measured on different scales.

## Software requirements

The analysis was conducted in Python. The main packages used include:

```text
python >= 3.9
pandas
numpy
scipy
statsmodels
scikit-learn
xgboost
matplotlib
seaborn
ptitprince
openpyxl
jupyter
```

To install the required packages, create a virtual environment and run:

```bash
pip install pandas numpy scipy statsmodels scikit-learn xgboost matplotlib seaborn ptitprince openpyxl jupyter
```

Then open the notebook:

```bash
jupyter notebook chd-srilanka_analysis.ipynb
```

Run the notebook cells sequentially to reproduce the result tables and figures.

## Data statement

The dataset included in this repository is intended to be de-identified. It should not contain participant names, phone numbers, addresses, exact dates of birth, national identity numbers, or other direct identifiers. Users should treat the data as health-related research data and use it only for academic, reproducibility, and non-commercial research purposes.

## Citation

If you use this repository, please cite the associated manuscript:

```text
Perera DS, Dinh T, Chandrasekara A, Lisik D, Zou D, Rathnayake KM.
On the Impact of Fruit and Vegetable Consumption on Coronary Heart Disease Risk Factors:
A Case Study from Sri Lanka.
Submitted manuscript.
```

This citation should be updated after publication.

## Contact

For questions about the study or dataset, please contact the corresponding author:

**Kumari Malkanthi Rathnayake, PhD (UK)**
Department of Nutrition and Dietetics
Faculty of Livestock, Fisheries and Nutrition
Wayamba University of Sri Lanka
Makandura (NWP), 60170, Sri Lanka

Email: `kumarimr@wyb.ac.lk`

## License

Please add a license file before final public release. If the repository is intended for open academic reuse, consider adding an MIT License for code and a separate data-use note for the dataset. If reuse of the dataset should be restricted, specify this clearly in a `LICENSE` or `DATA_USE.md` file.
