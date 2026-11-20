# Is the 60/40 Portfolio Still Diversified?

A short study of whether US bonds still diversify US equities, using 20 years of daily total returns.

## Finding

Since 2020, US stocks and bonds have moved together, so bonds have diversified a 60/40 portfolio far less than they used to.

| | 2004–2019 | 2020–2024 |
|---|---|---|
| Daily correlation | -0.12 (p = 0.11) | **+0.19** (p = 0.001) |
| Monthly correlation | 0.00 (p = 0.97) | **+0.57** (p < 0.001) |
| Monthly R-squared | 0.00 | **0.32** |

A single regression over 2004–2024 shows no daily relationship (correlation -0.01), because the two regimes cancel out.
Splitting the sample at 2020 reveals the shift.

## Key takeaways

- **Strongest at the monthly horizon,** where investors rebalance: since 2020, bond returns explain about a third of monthly stock returns.
- **A 20-year regression hides the shift.** The two regimes cancel out, so the full-period daily relationship looks like zero.
- **Robust to the window choice.** 3-, 6-, and 12-month rolling correlations all turn positive in early 2020 and stay mostly positive.
- **Inflation is the likely driver.** Stocks and bonds tend to move together when inflation is the main risk, as in 2021–2024.

![Rolling 90-day correlation](figures/Rolling%2090%20Day%20Correlation.png)

## Update through November 2026

A second notebook, `Stock Bond Correlation - updated to 11.20.2026.ipynb`, extends the data to the latest trading day and tests 2025 onward, a period the original study never saw.

| | 2020–Nov 2026 | 2025–Nov 2026 (out of sample) |
|---|---|---|
| Daily correlation | **+0.18** (p < 0.001) | **+0.18** (p = 0.005) |
| Monthly correlation | **+0.50** (p < 0.001) | +0.13 (p = 0.21, 23 months) |

The regime has persisted out of sample on daily data. The monthly link has weakened in 2025–2026 but is not yet conclusive.

## Data and method

- **Equities:** SPY (S&P 500 ETF). **Bonds:** AGG (US Aggregate Bond ETF). Adjusted closes, so returns include distributions.
- **Period:** AGG inception (late 2003) to December 31, 2024. Source: Yahoo Finance via `yfinance`.
- **Analysis:** full-period OLS regression (Newey-West standard errors), 63-, 126-, and 252-trading-day rolling correlations
  (about 3, 6, and 12 months), and
  separate regressions for 2004–2019 and 2020–2024 on daily and monthly returns.

## Run it

```bash
pip install -r requirements.txt
jupyter notebook "Stock Bond Correlation.ipynb"
```

Or open the notebook in [Google Colab](https://colab.research.google.com/) and choose **Runtime → Run all**.

## Limitations

- Two ETFs stand in for each asset class.
- The 2020 regime break is chosen by eye; a formal structural-break test is a natural next step.
- Adding inflation (CPI or breakevens) would test the most common explanation for the regime change.

---
Phillip Kim · [LinkedIn](https://www.linkedin.com/in/phillip-kim)
