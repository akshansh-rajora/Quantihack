Quantihack Trading Algo: Multi-Signal Production Engine
​This repository contains the high-frequency trading (HFT) algorithm developed for Quantihack 2025. The strategy utilizes a sophisticated multi-signal scoring engine, real-time surge detection, and automated volatility calibration to navigate volatile markets across 20+ asset classes, including Equities, Commodities, Forex, and Indices.

​📈 Performance & Potential Analysis
​Based on the production logic, this algorithm is designed for high-alpha capture with a focus on capital preservation:
​Initial Capital: The strategy is architected for a $1,000,000 starting cash position.
​Surge Profitability: The algorithm scales aggressively during high-volatility events, with a SURGE_NOTIONAL of $1,000,000 per trade when a move exceeds 5x the normal volatility.
​Risk Guardrails: A strict DAILY_LOSS_LIMIT of 20% ensures the algorithm halts before a total wipeout, while individual assets are "circuit-broken" after 3 consecutive losses.
​Scalability: With a BASELINE_NOTIONAL of $50,000 per standard trade and a capacity for 4 simultaneous positions, the algo maintains high turnover without over-leveraging.
​🛠 Strategy Components
​The algorithm operates on a three-phase execution cycle:

​1. Multi-Signal Scoring Engine
​The "Scan and Score" phase evaluates assets using a weighted ensemble of seven technical indicators:
​RSI (Relative Strength Index): Overbought/Oversold detection (Scales from score 1 to 5).
​Surge Detection: Identifying 5-10 tick "explosive" moves relative to learned volatility.
​Bollinger Bands: Mean reversion signals at the 0.95 and 0.10 percentiles.
​EMA Crossover: Golden Cross and Death Cross detection (8/21 period).
​Z-Score: Identifying statistical outliers in price action (thresholds at 1.5 and 2.0).
​Linear Regression: Slope and R^2 analysis to confirm trend strength.
​Momentum: Immediate short-term velocity checks across 5 and 20-tick windows.

​2. Advanced Risk Management
​Volatility Learning: Features a vol_cache that "learns" the unique volatility profile of each asset every 10 ticks, adjusting stop-losses and trailing stops dynamically.
​Trailing Stops: Implements a dynamic exit strategy once a position reaches 0.5% profit, protecting gains against sudden reversals.
​Time-Based Exits: A MAX_HOLD_TICKS of 200 (~2.5 minutes) prevents capital from being tied up in stagnant trades.
​3. Smart Position Sizing
​The algorithm scales its conviction based on signal strength. Standard signals trade the baseline, while high-conviction signals (score > 6 or > 10) or confirmed surges trigger increased notional sizing to maximize capture.

​🚀 Deployment
​The code is designed to interface directly with the quantihack API.
​Key Parameters: asset_vol, trailing_stop, stop_loss
​Max Positions: 4
​Max Spread: 0.6% (prevents slippage in illiquid markets)
​Minimum Score: 3.0 (filters out market noise)
​Developed by Priyanshu Sheshkar, Akhilesh Sakure, Akshansh Rajora
​Education: MSc Financial Technology with Data Science, University of Bristol.  
