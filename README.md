# Portfolio Risk Analytics & Stress Testing Engine

## Overview

A Python-based quantitative risk analytics framework applied to a
two-asset portfolio, using publicly traded ETFs as proxies for an
institutional-style equity/bond allocation. The project combines
standard market risk techniques with two extensions drawn from
insurance and actuarial risk management, in a style consistent with
risk analysis practices in banking, insurance, and reinsurance.

## Objectives

- Measure portfolio risk using multiple, complementary methods rather
  than a single estimate
- Validate model accuracy through formal statistical backtesting
- Evaluate portfolio behavior under real historical and hypothetical
  stress scenarios
- Connect standard market risk measures to an insurance-relevant
  perspective (interest rate duration risk, an illustrative Solvency
  II-style capital view, and tail-risk modeling)

## Portfolio

- **EUNL.DE** — iShares Core MSCI World UCITS ETF (global equity proxy)
- **EUN5.DE** — iShares Core € Corp Bond UCITS ETF (euro
  investment-grade corporate bond proxy)
- **Allocation**: constant-weight 60% equity / 40% bond
- **Data**: daily closing prices, January 2020 – September 2026 (1,694
  trading days after cleaning), via Yahoo Finance

## Methodology

- Return, volatility, and correlation analysis; portfolio construction
  and drawdown
- Value at Risk (VaR) and Expected Shortfall (ES) — historical,
  parametric (Variance-Covariance), and Monte Carlo methods
- Kupiec Proportion of Failures backtest to validate the VaR model
- Historical stress testing (COVID-19 crash, 2022 rate shock, 2022
  stock-bond selloff, 2025 tariff shock) and hypothetical single-day
  shock scenarios
- Market factor analysis (S&P 500, VIX, US 10-Year yield, EUR/USD) and
  a factor-based VIX stress scenario
- Interest rate duration shock on the bond position
- An illustrative one-year risk perspective (Solvency II-style framing,
  not a regulatory SCR calculation)
- Extreme Value Theory (Peaks-Over-Threshold, Generalized Pareto
  Distribution) for tail risk beyond the historical sample

## Key Results

- **Annualized volatility**: 10.9% (1.1 pp diversification benefit vs.
  the weighted average of the two assets)
- **Historical VaR 95%**: −0.99%
- **Historical VaR 99%**: −2.32%
- **Monte Carlo VaR (95% / 99%)**: −1.11% / −1.57%
- **Expected Shortfall, historical (95% / 99%)**: −1.71% / −3.23%
- **Kupiec backtest**: does not reject correct coverage of the
  historical VaR model at either the 95% or 99% level (p = 0.97 / 0.99)
- **EVT (Generalized Pareto, ξ ≈ 0.37)**: 99.5% VaR ≈ −2.73%, 99.9% VaR
  ≈ −5.19% — evidence of heavier tails than a Normal distribution
  implies
- **Stress testing**: worst historical scenario is the COVID-19 crash
  (−23.45%); the 2022 stock-bond selloff shows bonds losing more than
  equities, a breakdown in the usual diversification benefit

## Project Structure

```
Portfolio_Risk_Analytics_Stress_Testing/
├── README.md
├── Portfolio_Risk_Analytics_Stress_Testing.ipynb
├── Portfolio_Risk_Analytics_Report.pdf
├── requirements.txt
└── data/
    └── README.md
```

## Tools & Technologies

Python · pandas · numpy · matplotlib · seaborn · yfinance · scipy ·
statsmodels

## How to Run

1. Install dependencies: `pip install -r requirements.txt`
2. Open `Portfolio_Risk_Analytics_Stress_Testing.ipynb` in Jupyter or
   PyCharm.
3. Run all cells sequentially. All market data is downloaded
   automatically from Yahoo Finance at runtime — no manual data
   download is required.

## Limitations

- Portfolio weights are constant (closer to a daily-rebalanced
  allocation than true buy-and-hold), and returns are assumed
  frictionless (no transaction costs or liquidity constraints)
- Parametric VaR and Monte Carlo simulation assume normally
  distributed returns, which understates tail risk relative to the
  historical and EVT-based estimates
- The 99% VaR/ES and the EVT fit rely on a limited number of tail
  observations, introducing statistical uncertainty
- The bond duration (5.5 years) is an industry-typical estimate, not
  the fund's officially reported figure

Full discussion in the "Limitations & Assumptions" section of the
notebook.

## Disclaimer

This project is an independent academic and portfolio-building
exercise. It does not constitute investment advice, and the portfolio
does not represent the actual holdings of any institution. The
Solvency II-style figure is a simplified statistical illustration, not
a regulatory Solvency Capital Requirement (SCR) calculation. All data
is sourced from public providers (Yahoo Finance) for research purposes.

## Author

Khaled Salman — M.Sc. Quantitative Finance, Christian-Albrechts-Universität
zu Kiel
