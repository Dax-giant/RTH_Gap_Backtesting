# RTH Gap Backtesting

A Python-based backtesting project that tests a Regular Trading Hours (RTH) gap-fill strategy using historical intraday market data.

## Overview

The strategy identifies price gaps at the New York stock market open and attempts to trade their reversion toward the previous trading session's range.

The backtest uses one-minute OHLCV data and the `backtesting.py` library to simulate trades and evaluate strategy performance.

## Strategy Rules

* **Trading session:** New York RTH, 09:30–16:00.
* **Entry time:** 09:30 New York time.
* **Minimum gap:** 5.0 price units.
* **Gap up:** Enter short when the opening price is above the previous session's RTH high by more than the minimum gap.
* **Gap down:** Enter long when the opening price is below the previous session's RTH low by more than the minimum gap.
* **Take profit:** The previous session's RTH high for short trades or RTH low for long trades.
* **Stop loss:** Set at a distance equal to the gap size from the entry price.
* **Position management:** Close open positions at 15:59.

The strategy allows a maximum of one trade per day.

## Repository Structure

```text
RTH_Gap_Backtesting/
├── Untitled-1.ipynb    # Backtesting and strategy research
├── Untitled-1.html     # Exported notebook
├── Untitled-1.pdf      # PDF export
├── LICENSE             # MIT License
└── README.md           # Project documentation
```

## Requirements

* Python 3.11 or a compatible Python version
* Jupyter Notebook
* pandas
* NumPy
* Matplotlib
* backtesting.py

## Installation

Clone the repository:

```bash
git clone https://github.com/Dax-giant/RTH_Gap_Backtesting.git
cd RTH_Gap_Backtesting
```

Install the required packages:

```bash
pip install pandas numpy matplotlib backtesting jupyter
```

## Historical Data

The notebook loads historical market data from a CSV file named `data.csv`.

Place your data file in the project directory before running the notebook.

The CSV must contain these columns:

* `Date`
* `Open`
* `High`
* `Low`
* `Close`
* `tick_volume`

The `Date` column must contain timestamps that can be interpreted in New York market time.

**Important:** Ensure that your timestamps are correctly converted to the `America/New_York` time zone before calculating RTH levels. The strategy's session times must match the timestamps in your dataset.

## Running the Backtest

Start Jupyter Notebook:

```bash
jupyter notebook
```

Open `Untitled-1.ipynb` and execute the cells in order.

The notebook loads the historical data, calculates daily RTH highs and lows, executes the gap-fill strategy, and generates backtesting results.

## Customization

You can modify the strategy parameters in the notebook, including:

* Minimum gap size.
* Entry conditions.
* Stop-loss and take-profit calculations.
* Trading session times.
* Initial account balance.
* Commission assumptions.

## Disclaimer

This project is intended for educational and quantitative research purposes only.

Backtesting results do not guarantee future performance. Actual trading results may differ because of commissions, slippage, execution constraints, and market conditions.

Always validate the strategy using realistic trading costs and out-of-sample historical data before considering live deployment.
