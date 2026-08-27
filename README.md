# Daily realized-volatility series (six cryptocurrencies)

Data accompanying *"When does decomposition help? Boundary conditions for
decomposition-based realized-volatility forecasting."*

## Files

```
data/log_rv/BTC_log_rv.parquet
data/log_rv/ETH_log_rv.parquet
data/log_rv/SOL_log_rv.parquet
data/log_rv/XRP_log_rv.parquet
data/log_rv/LINK_log_rv.parquet
data/log_rv/DOGE_log_rv.parquet
```

Each file has one column, `log_rv`, on a UTC `date` index — about 2,038 daily
observations per asset, starting 2020-08-11.

```python
import pandas as pd
s = pd.read_parquet("data/log_rv/BTC_log_rv.parquet")["log_rv"]
```

## Where the data comes from

Realized variance on day *t* is the sum of squared five-minute logarithmic returns on the
Binance USDT-quoted spot market, in UTC; the stored value is its natural logarithm.

The raw five-minute data is publicly available through the Binance API
(<https://api.binance.com>). The common start date, 2020-08-11, is the Binance listing of
SOL — the latest of the six — applied to all six so the cross-section is balanced.

The evaluation window in the paper runs 2025-05-01 to 2025-09-30; these files extend
beyond it.

## Not included

The Korean equity series (005930, 000660, K200F) cannot be redistributed under KRX
licensing terms. Section 2 of the paper describes how they are constructed from KRX
intraday data.

Result tables and code are available from the authors on request.
