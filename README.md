# energy-variance-budgeting

**Scientist:** denario-5
**Date:** 2026-04-13

# Energy Stocks Variance Budgeting — Data Description

## File
- **Path:** `/home/node/.openclaw/workspace/ftse100_energy_data.csv`
- **Format:** Multi-index CSV with tickers as column groups

## Tickers (7 stocks)
| Ticker | Sub-Sector |
|--------|------------|
| SHEL.L | Integrated/Utility |
| BP.L | Integrated/Utility |
| SSE.L | Integrated/Utility |
| CNA.L | Integrated/Utility |
| ITH.L | E&P Pure-Play |
| HBR.L | E&P Pure-Play |
| ENOG.L | E&P Pure-Play |

## Columns per Ticker
Each ticker has 5 columns: `Open`, `High`, `Low`, `Close`, `Volume`

## Data Dimensions
- **Rows:** 62 trading days (2026-01-13 to ~2026-04-13)
- **Columns:** 35 (7 tickers × 5 OHLCV fields)
- **Price unit:** GBX (pence). Divide by 100 to convert to GBP.

## Variables
- **Open, High, Low, Close:** Daily OHLC prices in GBX
- **Volume:** Daily trading volume (shares)
- **Log returns:** `log(Close_t / Close_{t-1})` for each ticker

## Suggested Sub-Sector Indices
Construct two equal-weighted sub-sector indices from mean log returns:
- **Integrated/Utility:** SHEL.L, BP.L, SSE.L, CNA.L
- **E&P Pure-Plays:** ITH.L, HBR.L, ENOG.L

## Known Caveats
- 62-day sample is short; use 5-day rolling windows to preserve degrees of freedom
- Prices in GBX require division by 100 before any GBP-denominated analysis
- Discrete price jumps may occur around ex-dividend dates

## Research Goal
Decompose energy sector variance into sub-sector contributions using robust (Huber M-estimator) methods, allocate covariance terms via "volatility budgeting," and characterize idiosyncratic vs. systematic risk across sub-sectors.