# SE4 update for Data and Methods, Results, and Discussion

## Data and Methods update

Three reproducible figures were generated directly from the SE3 outputs using Python. Figure 1 used plant-specific validation predictions reconstructed from the SE3 OLS specification (`observed_daily_outflow ~ simulated_daily_outflow + sin_doy + cos_doy`) after chronological 80/20 train–validation splitting. Figure 2 used the SE3 fit-metric table to compare train and validation RMSE and KGE across plants. Figure 3 used the SE3 coefficient table to display plant-specific coefficient estimates and 95% HC3 robust confidence intervals for the fitted terms. No GUI-based software, basemaps, or post-hoc figure editing were used; all figures were exported directly from Python as PNG files.

## Results update

The figures show a consistent daily-skill pattern across the Oulujoki cascade. Validation RMSE ranged from 0.393 to 0.413, while validation KGE ranged from 0.588 to 0.605. The highest validation KGE was obtained at pyhäkoski. Figure 1 shows that most validation points follow the 1:1 line reasonably well, although scatter increases at higher daily outflows. Figure 2 shows that train skill is higher than validation skill for all plants, indicating some loss of generalization to later periods but not a breakdown of predictive structure. Figure 3 shows that the simulated daily outflow term is positive for every plant, with coefficients ranging from 0.717 to 0.786; its standardized effect size (0.775–0.807) exceeds the seasonal terms, indicating that the modelled daily release is the dominant driver of observed daily outflow.

## Discussion update

The figure set supports the interpretation that the SE3 daily models capture an important part of plant-level daily realism, but that daily agreement is still imperfect, especially during more extreme regulation periods. The dominance of the simulated daily outflow coefficient suggests that the operational model carries substantial explanatory value into the observation space, while the seasonal sine/cosine terms mainly correct for remaining periodic structure. The train–validation performance gap indicates that conclusions should be based primarily on validation figures and not calibration fit alone. Because the current comparison uses daily aggregation, the figures do not resolve sub-daily hydropeaking behavior; they instead evaluate whether the hourly operational outputs remain realistic after conversion to the temporal scale of the observations.
