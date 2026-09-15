<img width="1920" height="800" alt="banner (1)" src="https://github.com/user-attachments/assets/ee531597-445c-4476-bdb1-7d3dafc003b8" />

# 📈 Stock Market Analysis — Reading the Tape

> *A stock price is just a number until you watch it move. This notebook is about watching.*

---

## 📖 The Premise

Markets talk in a language made almost entirely of lines going up and down, but underneath every candle there's a quieter conversation — momentum against noise, conviction against panic, one ticker's story braided in with several others on the same trading day. `stock_market.ipynb` sits down with a year's worth of daily price data and listens to that conversation properly.

It's not trying to predict tomorrow's close. It's doing something more foundational: **teaching the data to show its own shape** — trend, comparison, and risk, laid out one visualization at a time.

---

## 🧪 What's Inside the Dataset

The notebook loads `stock_market_analysis.csv` — **1,950 daily records** across multiple tickers — and immediately profiles it with `df.info()` and `df.head()`, so the structure is transparent before a single chart gets drawn.

| Column | What it captures |
|---|---|
| `Date` | The trading day |
| `Ticker` | The stock symbol (AAPL is used as the featured example) |
| `Open` / `High` / `Low` / `Close` | The day's price range — where it started, peaked, dipped, and settled |
| `Adj Close` | Close price adjusted for splits/dividends |
| `Volume` | Shares traded that day |
| `Daily Return (%)` | Day-over-day percentage price change |
| `MA20` / `MA50` | 20-day and 50-day moving averages — the smoothed heartbeat under the noise |

Eleven columns, and almost every one of them earns its own chart later in the notebook.

---

## 🔬 The Investigation, Step by Step

### 1. Meet the Data
Before anything gets plotted, the notebook prints the full schema and a preview of the first rows — dtypes, null counts (note that `MA20`/`MA50` start out as `NaN`, since there simply aren't enough prior trading days yet to average), and a first look at AAPL's early-January prices.

### 2. 📉 The AAPL Trend Line — Signal Under the Noise
A focused single-ticker chart plots AAPL's **daily close price alongside its 20-day and 50-day moving averages**. The raw close is jagged and reactive; the moving averages cut through that noise and reveal the underlying trend — the classic technical-analysis move of asking *"where is this stock actually heading, once you stop overreacting to every single day?"*

### 3. 📊 Multi-Stock Comparison, Price on Top of Volume
A two-panel figure stacks two stories that always belong together:
- **Top:** closing prices for *every* ticker in the dataset, plotted on shared axes so relative performance is instantly comparable.
- **Bottom:** AAPL's daily trading volume as a bar chart beneath it, sharing the same time axis — so price movement and the *conviction* behind that movement (how many shares actually changed hands) can be read side by side.

### 4. 🎲 Daily Return Distributions — Measuring the Nerves
The closing act steps back from price entirely and looks at **volatility**: a step-histogram of daily percentage returns, one distribution per ticker, density-normalized so shape (not just scale) is comparable. A tall, narrow curve means a calm stock; a wide, flat one means a stock that keeps its shareholders up at night. This is where the notebook quietly answers "which of these stocks is *riskier*?" — without ever needing to say the word.

---

## 🛠️ Under the Hood

- **Language:** Python 3
- **Libraries:** `pandas` for data handling, `numpy` for array math, `matplotlib` + `seaborn` for every visual
- **Techniques on display:** moving-average smoothing, multi-panel shared-axis subplots, categorical multi-line comparison, and normalized histogram distributions
- **Runtime:** built and last run in a Colab environment — runs top to bottom in well under a minute

---

## 🚀 Running It Yourself

```bash
# 1. Set up the environment
pip install pandas numpy matplotlib seaborn

# 2. Make sure the dataset sits next to the notebook
#    (the notebook expects: stock_market_analysis.csv)

# 3. Launch and run all cells
jupyter notebook stock_market.ipynb
```

Run the cells in order — the notebook builds a narrative: **load → zoom into one stock's trend → zoom out to compare all stocks and their volume → zoom into risk.** Each section trades a bit of detail for a bit more perspective.

---

## 🌍 Why This Kind of Analysis Matters

Every trading desk, every robo-advisor, every "should I buy this dip" gut-check ultimately rests on the same three primitives this notebook visualizes: **trend, relative performance, and volatility.** None of them require a model to compute — they just require someone to actually *plot the data and look at it*, which is rarer than it should be. This notebook is that look: unhurried, unopinionated, and built to hand the real decision-making back to a human who now has a much clearer picture than a raw CSV ever gave them.

---

## 💡 Ideas for Extending It

- Add a rolling volatility band (Bollinger-style) around the moving averages in the AAPL chart
- Compute cumulative returns per ticker to compare *total* performance over the year, not just daily swings
- Correlate daily returns *across* tickers — do these stocks move together, or independently?
- Layer in a drawdown chart to show each stock's worst peak-to-trough stretch

---

<p align="center"><i>The chart doesn't predict the market. It just finally lets you see it.</i></p>
