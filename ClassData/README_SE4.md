# SE4: Figures and data-story package based on SE3

This package generates reproducible figures from the SE3 daily model-comparison workflow.

## Purpose

The goal of SE4 is to turn the SE3 outputs into figures that communicate the main data story:
1. how closely plant-specific daily predictions reproduce observed daily outflow during validation,
2. how model skill changes from training to validation, and
3. which fitted terms dominate the plant-specific OLS models.

## Inputs

Place these files in the same parent directory as this package, or update the paths in the notebook:

- `daily_comparison_long.csv`
- `fit_metrics.csv`
- `coefficients.csv`

These files were produced in SE3 from:
- `Estimated hourly.xlsx` (hourly simulated output)
- `Observed daily.xlsx` (daily observations)

## Outputs

Running the notebook saves digital figures to `images/`:

- `images/figure1_validation_scatter_by_plant.png`
- `images/figure2_skill_summary_by_plant.png`
- `images/figure3_coefficients_by_plant.png`

It also writes:
- `captions_SE4.md`
- `docs/SE4_methods_results_discussion_update.md`

## Exact figure workflow

### Data-processing assumptions inherited from SE3
- Simulated hourly outflow was aggregated to **daily mean** because the values behave like discharge-rate variables rather than daily volumes.
- Days with incomplete hourly records at the start and end of the record were excluded before daily comparison.
- Plant-specific OLS models were fit with the formula:

`observed_daily_outflow ~ simulated_daily_outflow + sin_doy + cos_doy`

- The first 80% of each plant record was used for training and the final 20% for validation.
- Robust standard errors were computed with `cov_type="HC3"`.

### Python functions used for figure generation
- `pandas.read_csv()` to load SE3 outputs
- `statsmodels.formula.api.ols()` to reconstruct plant-specific fitted values used in Figure 1
- `matplotlib.pyplot.scatter()` for the validation scatterplots and skill dot plots
- `matplotlib.axes.Axes.errorbar()` for coefficient estimates with 95% confidence intervals
- `matplotlib.figure.Figure.savefig()` to export the final figures as PNG files

## GUI software, basemaps, and ancillary layers

None were used.
- No GIS basemaps were used.
- No GUI-only processing was required.
- All visual elements were generated directly in Python from the SE3 outputs.

## Post-hoc graphical processing

None.
The saved PNG files are the direct outputs from Python and were not edited in Illustrator, PowerPoint, Photoshop, or other external software.

## Reproducibility

Open and run `SE4_Results Visualization.ipynb` from top to bottom. The notebook regenerates the figures exactly from the SE3 CSV outputs.
