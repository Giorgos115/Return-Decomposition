Return Decomposition
====================

Purpose
-------
A transparent, reproducible, returns-based attribution tool: Estimate a manager's factor exposures,
decompose monthly returns into factor group contributions vs residual, and
summarize performance + explanatory power (R²) with rolling analyses and plots.

Inputs
------
- fund_returns.csv   : columns = ["datetime", "<Fund Name>", ...] (monthly %)
- factor_returns.csv : columns = ["datetime", <Factor1>, <Factor2>, ...] (monthly %)
- factors_meta.json  : {"<Factor>": {"group": "<GroupName>"}, ...}

Notes
-----
• CSVs are assumed to store returns as PERCENT strings (e.g. "0.85%").
  We convert them to decimal floats (0.0085).
• The script uses ElasticNetCV for robust exposure estimation and rolls a
  36M training window with a 1M test horizon.
• Plots summarize cumulative decomposition, average contributions, explained
  vs residual, rolling R², and a heatmap of rolling factor betas.
