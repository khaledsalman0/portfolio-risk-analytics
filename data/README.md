# Data

This project does not store raw market data in the repository.

All price data (EUNL.DE, EUN5.DE, and the market factors used in Section
6 of the analysis: ^GSPC, ^VIX, ^TNX, EURUSD=X) is downloaded
automatically from Yahoo Finance via the `yfinance` library when the
notebook is run — see the "Data Acquisition" section of
`Portfolio_Risk_Analytics_Stress_Testing.ipynb`.

Re-running the notebook end-to-end will regenerate all data locally; no
manual download or setup is required beyond an internet connection.

