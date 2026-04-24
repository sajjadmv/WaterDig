## 9) README

### Inputs
- `Estimated hourly.xlsx`
- `Observed daily.xlsx`

### Core workflow
1. Read hourly simulated plant outputs and observed daily plant outputs.
2. Harmonize plant names.
3. Aggregate simulated hourly outputs to daily mean values.
4. Remove incomplete edge days.
5. Merge daily simulated values with daily observed values by `Date`.
6. Fit one OLS model per plant:

   `observed_daily_outflow ~ simulated_daily_outflow + sin_doy + cos_doy`

   using HC3 robust standard errors and a chronological 80/20 train/validation split.
7. Export coefficients, fit metrics, predictions, and model summaries.

### Outputs
- `model_data/evaluation/daily_simulated_from_hourly.csv`
- `model_data/evaluation/daily_comparison_wide.csv`
- `model_data/evaluation/daily_comparison_long.csv`
- `model_data/statistical_model/coefficients.csv`
- `model_data/statistical_model/fit_metrics.csv`
- `model_data/statistical_model/predictions.csv`
- `model_data/statistical_model/model_summary.txt`
- `model_data/statistical_model/model_manifest.json`