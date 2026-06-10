# nutrition-chd-srilanka

This repository contains the data files, analysis notebook, result tables, and figures associated with the manuscript:

**On the Impact of Fruit and Vegetable Consumption on Coronary Heart Disease Risk Factors: A Case Study from Sri Lanka**

The study examines how total fruit and vegetable intake relates to dietary nutrient profiles and cardiometabolic risk markers in a cross-sectional sample of Sri Lankan adults. The analysis includes exploratory data analysis, Spearman correlation analysis, energy-adjusted nutrient analyses, between-strata heterogeneity testing, regression-based sensitivity checks, female-only sensitivity analysis, and supervised regression modelling.

## Repository contents

### Analysis notebook

* `chd-srilanka_analysis.ipynb`
  Main Jupyter notebook used to generate the analyses, tables, and figures reported in the manuscript.

### Data files

* `heart_new.xlsx`
  Main data file used for the analyses.

* `heart_filtered.csv`
  Main analytic dataset used after applying the inclusion criteria for the primary analyses.

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
  Between-strata heterogeneity tests comparing correlations in the `<= 200 g/day` and `> 200 g/day` groups.

* `linear_reg_total_quantity_confounding_checks.csv`
  Regression-based sensitivity analyses assessing associations between total fruit and vegetable intake and selected cardiometabolic endpoints before and after covariate adjustment.

* `model_evaluation_results_fullsample.csv`
  Supervised regression model evaluation results for the full analytic sample.

* `model_evaluation_results.csv`
  Supervised regression model evaluation results for additional subgroup or sensitivity analyses.

### Figure files

* `violin_total_by_strata.pdf`
  Distribution of fruit, vegetable, and total fruit and vegetable intake by intake stratum.

* `raincloud_leq200.pdf`
  Raincloud plots for study variables in the `<= 200 g/day` stratum.

* `raincloud_g200.pdf`
  Raincloud plots for study variables in the `> 200 g/day` stratum.

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

The analysis workflow includes the following steps:

1. Load the main study data file.
2. Prepare the analytic dataset for the main statistical analyses.
3. Define total fruit and vegetable intake in grams per day as the primary dietary exposure.
4. Stratify participants into:

   * `<= 200 g/day`
   * `> 200 g/day`
5. Summarize fruit, vegetable, and total fruit and vegetable intake distributions.
6. Estimate Spearman correlations between total fruit and vegetable intake and study variables.
7. Perform energy-adjusted nutrient analyses using:

   * nutrient-density method
   * residual method
8. Compare correlation patterns between intake strata using heterogeneity tests.
9. Perform regression-based sensitivity analyses adjusted for age, sex, and total energy intake.
10. Conduct a female-only sensitivity analysis.
11. Benchmark supervised regression models for selected cardiometabolic and dietary endpoints.
12. Generate the result tables and figures reported in the manuscript.

## Machine-learning models

The supervised regression benchmark includes:

* Lasso
* Ridge
* Bayesian Ridge
* Random Forest
* Support Vector Regression with a linear kernel
* XGBoost

Model performance is evaluated using held-out test `R^2` and root mean squared error (RMSE). Because the outcomes are measured on different scales, RMSE should be interpreted within each endpoint rather than compared directly across endpoints.

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

To install the required packages, run:

```bash
pip install pandas numpy scipy statsmodels scikit-learn xgboost matplotlib seaborn ptitprince openpyxl jupyter
```

To reproduce the analysis, open the notebook:

```bash
jupyter notebook chd-srilanka_analysis.ipynb
```

Then run the notebook cells sequentially.

## Citation

If you use this repository, please cite the associated manuscript:

@misc{dinh2026nutritionchdsrilanka, author = {Dinh, Tai and Perera, Dilki S. and Chandrasekara, Ananda and Lisik, Daniil and Zou, Ding and Rathnayake, Kumari M.}, title = {nutrition-chd-srilanka: Analysis files, result tables, and figures for a study of fruit and vegetable intake and cardiometabolic risk markers in Sri Lankan adults}, year = {2026}, publisher = {GitHub}, url = {https://github.com/taiduydinh/nutrition-chd-srilanka} }
