# Crypto Sell-Off Mean Reversion Backtest

This project extends my previous crypto sell-off mean reversion study by converting the event-study findings into a simple rules-based backtest.

The project tests whether buying BTC, ETH or SOL after a large daily sell-off would have produced attractive historical returns across different holding periods, after accounting for transaction costs, drawdowns and market exposure.

## Research Question

If an investor bought BTC, ETH or SOL after a daily sell-off of 10% or more, would the strategy have produced attractive historical returns across different holding periods?

## Strategy Rules

The strategy follows a simple rules-based framework:

* A buy signal occurs when the asset falls by 10% or more in one day.
* The strategy enters at the signal-day close.
* The strategy exits after a fixed holding period.
* The holding periods tested are 1 day, 3 days, 7 days and 30 days.
* The strategy avoids overlapping trades.
* A transaction cost is applied to each trade.
* The starting portfolio value is set at £10,000.
* The strategy is tested both with and without a 50-day moving average trend filter.

## Assets Tested

The backtest covers:

* BTC
* ETH
* SOL

Daily price data is downloaded using `yfinance`.

## What The Project Measures

The notebook evaluates each strategy using:

* Number of trades
* Final portfolio value
* Total return
* Win rate
* Average trade return
* Worst trade
* Best trade
* Maximum drawdown
* Return-to-drawdown score
* Time in market
* Buy-and-hold benchmark comparison
* Selected strategy equity curves

## Main Findings

BTC produced the cleanest and most controlled mean-reversion profile under the rules tested, particularly over shorter holding periods and when using the 50-day moving average filter.

SOL produced the strongest raw strategy returns, especially over 3-day, 7-day and 30-day holding periods. However, these returns came with much larger drawdowns and more severe worst-trade outcomes, making SOL a higher-risk version of the strategy.

ETH was the weakest asset under this framework. Several ETH strategies, especially those using longer holding periods, produced weaker total returns and weaker risk-adjusted results.

The buy-and-hold benchmark produced much higher raw returns for BTC and SOL over the full sample period. However, this comparison is not perfectly like-for-like because buy-and-hold assumes continuous exposure from the first available date in each asset’s dataset, while the sell-off strategy is only invested after specific -10% sell-off signals.

The exposure analysis shows that the sell-off strategy spent only a small proportion of the full sample period invested in the market. This means it should be interpreted as a tactical mean-reversion strategy rather than a direct replacement for long-only buy-and-hold exposure.

## Tools Used

* Python
* pandas
* matplotlib
* yfinance
* Google Colab

## Key Limitations

This is a simplified historical backtest and has several important limitations.

The strategy enters at the signal-day close. In live trading, an investor may not know the final daily return until the close has occurred, meaning the exact closing price may not be achievable in practice.

The analysis uses daily price data rather than intraday data. This means it does not capture intraday volatility, liquidity conditions, bid-ask spreads or exact execution timing.

Transaction costs are simplified. The model applies a fixed transaction cost, but real trading costs can vary depending on exchange fees, spreads, slippage, volatility and order size.

The buy-and-hold benchmark is not a perfect like-for-like comparison because each asset is held from the first available date in its dataset. This naturally favours assets that experienced large long-term bull markets from early in their trading history.

The strategy does not include advanced risk management rules such as stop losses, take profits, volatility-adjusted position sizing or portfolio-level allocation.

Historical results do not guarantee future performance.

## Possible Improvements

Future versions of this project could improve the backtest by:

* Entering trades at the next day’s open rather than the signal-day close.
* Using intraday data to test more realistic execution assumptions.
* Adding stop losses and take-profit rules.
* Testing volatility-adjusted position sizing.
* Comparing results using the same start date across BTC, ETH and SOL.
* Building a portfolio-level version that allocates capital across multiple assets.
* Adding annualised return, Sharpe ratio and Calmar ratio metrics.

## Disclaimer

This project is for educational and research purposes only. It is not financial advice, investment advice or a recommendation to buy or sell any crypto asset.

Cryptoassets are highly volatile and can result in substantial losses. The results shown in this project are based on historical data and simplified assumptions. They should not be relied upon for live trading or investment decisions.
