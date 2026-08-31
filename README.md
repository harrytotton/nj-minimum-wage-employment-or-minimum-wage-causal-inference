# nj-minimum-wage-employment-or-minimum-wage-causal-inference
Causal inference analysis of NJ’s 2019 minimum wage increase using DiD and synthetic control”
Minimum Wage and Employment: A Causal Inference
Analysis (NJ vs PA)
Question
Does raising the minimum wage cause a reduction in employment in low-wage sectors? This
project tests that question using New Jersey’s 2019 minimum wage law as a natural
experiment.
Setup
New Jersey passed a law in February 2019 raising its minimum wage in stages, starting with
an increase from $8.85 to $10.00 on July 1, 2019, en route to $15.00 by 2024. Pennsylvania,
its neighboring state, kept the federal minimum wage of $7.25 unchanged throughout. This
mirrors the design of Card & Krueger’s influential 1994 study, updated with more recent
data.
Data: Monthly Accommodation & Food Services employment (thousands of persons,
seasonally adjusted), sourced from the Bureau of Labor Statistics via FRED, January 2015–
February 2020 (window chosen to avoid the COVID-19 employment shock).
Treatment date: July 1, 2019 (NJ’s first wage increase under the new law).
Methods
Two independent causal inference approaches were used to cross-check the result:
1. Difference-in-Differences (DiD) Compares the change in NJ’s employment before vs.
after July 2019 to the equivalent change in Pennsylvania, isolating the effect attributable to
the wage law rather than shared economic trends. Standard errors were adjusted for
autocorrelation (HAC/Newey-West) given the low Durbin-Watson statistic in the initial OLS
specification, which indicated the naive standard errors were unreliable for monthly time-
series data.
2. Synthetic Control Rather than relying on a single comparison state, a “synthetic NJ” was
constructed as a weighted blend of Kansas (81.3%) and Texas (18.7%) — two federal-
minimum-wage states, weighted to minimize the squared difference from NJ’s actual pre-
treatment employment path. The post-treatment gap between real NJ and this synthetic
counterfactual is the effect estimate.
Results
Method Estimate Significance / Pattern
Difference-in-
Differences
+2.56k jobs (SE, HAC-
adjusted) p = 0.51 — not statistically significant
Synthetic
Control
−1.72k jobs (average
post-period gap)
Sign flips from negative to positive over the
post-period; not a consistent effect
Both methods agree: there is no robust evidence that New Jersey’s minimum wage
increase reduced employment in the accommodation and food services sector, relative to
a credible counterfactual, in the eight months following the policy change.
Limitations
Short post-treatment window (8 months) before COVID-19 disrupted the series, limiting
statistical power to detect a small effect.
Two-state DiD relies on Pennsylvania alone as a comparison; the synthetic control
addresses this but is itself built from only two donor states.
Effects on employment hours or wages (as opposed to headcount) are not tested here.
Files
analysis.ipynb control construction, visualizations)
— full analysis notebook (data pull, cleaning, DiD regression, synthetic
README.md — this file
