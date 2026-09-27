# Portfolio Risk Analytics & Stress Testing Engine

### Python-based quantitative risk analytics with an insurance and reinsurance risk perspective

## Overview

A Python-based quantitative risk analytics framework applied to a two-asset equity/bond portfolio using publicly traded ETFs as market proxies.

The project combines standard market risk techniques with insurance- and actuarial-oriented extensions, including **Value at Risk (VaR), Expected Shortfall, Monte Carlo simulation, VaR backtesting, stress testing, interest-rate duration risk, Extreme Value Theory (EVT), and an illustrative Solvency II-style risk perspective**.

The objective is to examine how different risk measures behave under normal market conditions, historical stress events, and extreme tail scenarios.

---

## Key Findings

* **Portfolio annualized volatility:** 10.9%
* **Diversification benefit:** 1.1 percentage points versus the weighted average of the two assets
* **Historical VaR (95%):** −0.99%
* **Historical VaR (99%):** −2.32%
* **Monte Carlo VaR (95% / 99%):** −1.11% / −1.57%
* **Historical Expected Shortfall (95% / 99%):** −1.71% / −3.23%
* **Kupiec backtest:** does not reject correct unconditional coverage at either the 95% or 99% confidence level
* **EVT (GPD):** 99.5% VaR ≈ −2.73%; 99.9% VaR ≈ −5.19%
* **COVID-19 stress scenario:** −23.45% portfolio impact
* **2022 stock-bond selloff:** bonds lost more than equities during the selected stress period

The EVT results illustrate how model-based tail estimates can extend beyond the losses directly observed in the historical sample.

---

## Objectives

* Measure portfolio risk using multiple complementary approaches rather than a single risk measure
* Evaluate VaR breach frequency through formal statistical backtesting
* Measure Expected Shortfall to assess losses beyond VaR thresholds
* Evaluate portfolio behaviour under historical and hypothetical stress scenarios
* Analyse market-factor relationships and interest-rate sensitivity
* Connect standard market-risk analysis with insurance and reinsurance risk concepts
* Explore extreme tail losses using Extreme Value Theory

---

## Portfolio

The analysis uses two publicly traded ETFs as simplified market proxies:

* **EUNL.DE** — iShares Core MSCI World UCITS ETF, used as a global equity proxy
* **EUN5.DE** — iShares Core € Corp Bond UCITS ETF, used as a euro investment-grade corporate bond proxy

**Allocation:** Constant-weight 60% equity / 40% bond

**Data period:** January 2020 – September 2026

**Observations:** 1,694 trading days after data cleaning

**Data source:** Yahoo Finance

The portfolio is an illustrative analytical construction and does not represent the actual holdings of any institution.

---

## Methodology

### Portfolio & Market Risk

* Return, volatility, correlation, and drawdown analysis
* 60/40 portfolio construction
* Historical, parametric, and Monte Carlo Value at Risk
* Expected Shortfall

### Model Validation

* Kupiec Proportion of Failures backtest
* Evaluation of VaR breach frequency at the 95% and 99% confidence levels

### Stress Testing

* COVID-19 crash
* 2022 rate and inflation shock
* 2022 stock-bond selloff
* 2025 tariff shock
* Hypothetical single-day shock scenarios

### Market Factor Analysis

* S&P 500
* VIX
* US 10-Year Treasury yield
* EUR/USD
* VIX-based factor sensitivity analysis

### Interest Rate Risk

* Approximate bond duration analysis
* Parallel interest-rate shock scenarios

### Insurance Risk Perspective

* Illustrative one-year risk perspective
* Solvency II-style framing
* Explicit distinction between the project's simplified calculation and a regulatory SCR calculation

### Extreme Value Theory

* Peaks-Over-Threshold (POT)
* Generalized Pareto Distribution (GPD)
* Tail-risk estimation beyond the observed historical sample

---

## Analysis Workflow

The analysis follows the workflow below:

1. **Data acquisition and cleaning**
2. **Return calculation and exploratory analysis**
3. **Portfolio construction**
4. **Volatility, correlation, and drawdown analysis**
5. **VaR and Expected Shortfall estimation**
6. **Kupiec VaR backtesting**
7. **Historical and hypothetical stress testing**
8. **Market-factor analysis**
9. **Interest-rate duration risk**
10. **Illustrative Solvency II-style risk perspective**
11. **Extreme Value Theory tail-risk modelling**
12. **Interpretation and limitations**

This workflow is implemented in the main Jupyter notebook.

---

## Project Structure

```text
Portfolio_Risk_Analytics_Stress_Testing/
├── README.md
├── Portfolio_Risk_Analytics_Stress_Testing.ipynb
├── Portfolio_Risk_Analytics_Report.pdf
├── requirements.txt
└── data/
    └── README.md
```

### Main files

* **README.md** — Project overview, methodology, results, and documentation
* **Portfolio_Risk_Analytics_Stress_Testing.ipynb** — Complete Python analysis
* **Portfolio_Risk_Analytics_Report.pdf** — Detailed quantitative risk report
* **requirements.txt** — Python dependencies
* **data/README.md** — Information about the data directory and data handling

---

## Tools & Technologies

**Python · pandas · NumPy · matplotlib · seaborn · SciPy · yfinance**

The project focuses on practical applications of quantitative finance, financial risk analytics, statistical modelling, and insurance risk analysis.

---

## How to Run

### 1. Install dependencies

```bash
pip install -r requirements.txt
```

### 2. Open the notebook

Open:

```text
Portfolio_Risk_Analytics_Stress_Testing.ipynb
```

in Jupyter Notebook, JupyterLab, or PyCharm.

### 3. Run the analysis

Run the cells sequentially.

Market data is downloaded automatically from Yahoo Finance at runtime, so no manual data download is required.

---

## Limitations

* Portfolio weights are held constant at 60/40, which is closer to a daily-rebalanced allocation than a true buy-and-hold portfolio.
* Transaction costs and liquidity constraints are not modelled.
* Parametric VaR and Monte Carlo simulation assume normally distributed returns.
* Historical tail estimates and the EVT fit are subject to statistical uncertainty due to the limited number of extreme observations.
* The EVT results depend on the selected Peaks-Over-Threshold threshold.
* The bond duration of 5.5 years is an industry-typical approximation rather than the fund's officially reported duration.
* The ETFs are simplified market proxies and do not represent a fully diversified institutional portfolio.
* The one-year Solvency II-style figure is a simplified statistical illustration and does not reproduce the regulatory Solvency II SCR methodology.

A more detailed discussion of assumptions and limitations is provided in the project report and notebook.

---

## Disclaimer

This project is an independent academic and portfolio-building exercise.

It does not constitute investment advice, and the portfolio does not represent the actual holdings of any institution.

The Solvency II-style analysis is an illustrative statistical perspective and **not a regulatory Solvency Capital Requirement (SCR) calculation**.

All market data is obtained from public sources and is used for research and educational purposes.

---

## Author

**Khaled Salman**

M.Sc. Quantitative Finance
Christian-Albrechts-Universität zu Kiel

GitHub: [@khaledsalman0](https://github.com/khaledsalman0)
