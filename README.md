# Trader Performance vs Market Sentiment Analysis

Analyzes how Bitcoin market sentiment (Fear & Greed Index) affects trader behavior and performance on Hyperliquid, combining historical trade data with daily sentiment to surface patterns and actionable strategy recommendations.

## Datasets

- **Historical Trader Data** (`data/historical_data.csv`) — account, execution price, size, direction, closed PnL, fee, timestamp
- **Bitcoin Fear & Greed Index** (`data/fear_greed_index.csv`) — date, index value, sentiment classification

> Leverage was listed as an example metric in the brief but is not present in the trader dataset, so leverage distribution was not analyzed. All other required metrics are covered.

## Methodology

1. Loaded and explored both datasets; checked missing values and duplicates.
2. Converted timestamps, created a common `Date` column, merged the two datasets.
3. Engineered features: Trade Result, Daily PnL, Win Rate, Avg Trade Size, Trade Count, Long/Short Ratio, Drawdown Proxy.
4. Ran EDA comparing activity, profitability, win rate, and trade size across Fear vs. Greed.
5. Segmented traders (below) and extracted insights and strategy recommendations.
6. Bonus: clustering, predictive modeling, time-series analysis.

## Trader Segmentation

- **Required (threshold-based):** Frequent vs. Infrequent, High vs. Low Profit, High vs. Low Win Rate
- **Bonus (clustering):** Compared K-Means, Agglomerative, and DBSCAN by Silhouette Score — Agglomerative performed best, producing three archetypes: Conservative, Active High-Volume, and Large Position Traders

## Key Insights

1. Fear conditions saw the highest trading activity.
2. Greed conditions produced the highest average profitability, despite fewer trades.
3. Trade frequency, size, and direction all shift with sentiment.
4. Trading performance varies widely across individual traders.
5. Downside risk (drawdown proxy) is largest during Fear.

## Strategy Recommendations

1. **Trade cautiously during Fear** — apply tighter risk management (smaller sizing, stop-losses), since Fear carries the highest volatility and downside risk.
2. **Lean into Greed selectively** — Greed periods show the best average returns, so consider holding or sizing up in historically stronger-performing trader segments.

## Bonus Work

- **Predictive modeling:** Random Forest, XGBoost, LightGBM compared — Random Forest performed best (Accuracy, Precision, Recall, F1, ROC-AUC)
- **Time-series analysis:** daily average PnL trend, best/worst trading days

## Repository Structure

```
Trader-Performance-vs-Market-Sentiment/
├── Internship_assignment.ipynb
├── README.md
├── requirements.txt
├── data/
│   ├── historical_data.csv
│   └── fear_greed_index.csv
└── images/
```

## How to Run

```bash
git clone <repository-link>
pip install -r requirements.txt
jupyter notebook
```

Run top to bottom, with `historical_data.csv` and `fear_greed_index.csv` in `data/`.

## Libraries

Python, Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, XGBoost, LightGBM

## Conclusion

Market sentiment measurably affects trading activity, profitability, and behavior — Fear brings more activity and more risk, Greed brings fewer trades but better average returns. These patterns translate directly into the sentiment-aware risk recommendations above.
