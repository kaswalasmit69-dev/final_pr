<img width="1920" height="800" alt="banner" src="https://github.com/user-attachments/assets/7a945d0a-8713-44eb-b117-ac3ca37cd936" />

# 🌫️ Air Quality Analysis — Breathing Data, Reading the Sky

> *Somewhere between a weather report and a public-health warning, there's a dataset. This notebook goes looking for the story hiding inside it.*

---

## 📖 The Premise

Every city breathes differently. Some mornings the sky over New York is postcard-blue; other days it wears a grey haze like a bad mood it can't shake. Behind every one of those skies is a number — the **Air Quality Index (AQI)** — and behind every number is a small cascade of consequences: pollutants rising, weather shifting, and somewhere across town, a few more people walking into an ER with a cough that won't quit.

`Air_quality.ipynb` is an investigation into that cascade. It takes a year's worth of daily environmental readings and asks a handful of very human questions:

- Is the air getting better or worse over time — and does it depend on *where* you're standing?
- Does the weather itself let pollution off the hook, or make it worse?
- And — the question that actually matters — does dirtier air put more people in the hospital?

It's a short notebook, but it's built like a magnifying glass: point it at a CSV, and a whole invisible layer of atmosphere snaps into focus.

---

## 🧪 What's Inside the Dataset

The notebook loads `air_quality_analysis.csv` — **1,080 daily records** — and immediately profiles it (`df.info()`, `df.head()`) so nothing about the data's shape is a mystery before the analysis begins.

| Column | What it captures |
|---|---|
| `Date` | The day of observation |
| `Location` | City/monitoring site |
| `AQI` | The headline number — overall Air Quality Index |
| `PM2.5 (ug/m3)` / `PM10 (ug/m3)` | Fine and coarse particulate matter — the stuff that gets into lungs |
| `NO2 (ppb)` / `SO2 (ppb)` / `CO (ppm)` / `O3 (ppb)` | The gaseous pollutant lineup: nitrogen dioxide, sulfur dioxide, carbon monoxide, ozone |
| `Temperature (C)` / `Humidity (%)` / `Wind Speed (km/h)` | The weather context that pollution never exists apart from |
| `Respiratory Hospital Visits` | The human cost — daily count of related hospital visits |

Thirteen columns. One quiet thesis: *air is never just air — it's chemistry, weather, and consequence, all logged on the same day.*

---

## 🔬 The Investigation, Step by Step

### 1. Meet the Data
Before any chart is drawn, the notebook prints a full structural summary and a preview of the first five rows — dtypes, null counts, the works. No plot gets trusted until the table behind it has been read.

### 2. 📈 The AQI Timeline — Watching the Sky Change
A multi-line time series plots **AQI across every location, over the full date range**, each city given its own colored thread. Laid side by side, the lines stop being abstract numbers and start looking like weather itself — spikes, lulls, seasonal drift, one city's air behaving nothing like another's.

### 3. 🌡️ Three Scatterplots, Three Relationships
A single figure, split into three side-by-side lenses:
- **AQI vs. Temperature** — does the air quality index rise and fall with the thermometer?
- **AQI vs. Wind Speed** — does a breezy day actually clear the air, or is that just folklore?
- **AQI vs. Respiratory Hospital Visits** — plotted with a regression line, this is the panel with teeth: it asks directly whether worse air quality tracks with more people needing medical care.

### 4. 🔥 The Correlation Heatmap — Everything, All at Once
The finale zooms out to a full correlation matrix across every numeric column — pollutants, weather, and health outcomes — rendered as a red-blue heatmap with the coefficients annotated in place. It's the moment where every question asked earlier in isolation gets checked against everything else, simultaneously. One glance answers what a dozen individual scatterplots would take forever to show.

---

## 🛠️ Under the Hood

- **Language:** Python 3
- **Libraries:** `pandas` for wrangling, `matplotlib` + `seaborn` for every visual
- **Techniques on display:** time-series line plots with categorical hue, multi-panel scatter/regression figures, and a full Pearson correlation heatmap
- **Runtime:** built and last run in a Colab environment — lightweight enough to execute top to bottom in well under a minute

---

## 🚀 Running It Yourself

```bash
# 1. Set up the environment
pip install pandas matplotlib seaborn

# 2. Make sure the dataset sits next to the notebook
#    (the notebook expects: air_quality_analysis.csv)

# 3. Launch and run all cells
jupyter notebook Air_quality.ipynb
```

Run every cell in order — the notebook is intentionally linear: **load → visualize trends → probe relationships → correlate everything.** Each cell hands the next one a slightly sharper picture of the same story.

---

## 🌍 Why This Kind of Analysis Matters

Air quality data is one of those rare datasets where the abstraction (a three-digit index) and the reality (someone's asthma acting up on a smoggy Tuesday) are never more than one chart away from each other. This notebook doesn't try to be a definitive epidemiological study — it's smaller and more honest than that. It's an exploratory pass, the kind you'd run *before* the real modeling starts, built to answer a simple question well:

**When the air gets worse, what else moves with it?**

The heatmap at the end doesn't just report numbers — it's the closest thing this notebook has to an answer.

---

## 💡 Ideas for Extending It

- Layer in a rolling 7-day average to smooth the AQI timeline and expose seasonal trend lines
- Break the health-outcome regression out **per location**, since pollution's effect on hospital visits may not be uniform across cities
- Bring in a categorical AQI bucket (Good / Moderate / Unhealthy / Hazardous) and compare hospital visit rates *by category* rather than as a continuous regression
- Add a lag analysis — does today's AQI predict *tomorrow's* hospital visits better than same-day?

---

<p align="center"><i>Data tells you what happened. This notebook is just trying to help you notice.</i></p>

# 🌫️ Air Quality Analysis — Breathing Data, Reading the Sky

> *Somewhere between a weather report and a public-health warning, there's a dataset. This notebook goes looking for the story hiding inside it.*

---

## 📖 The Premise

Every city breathes differently. Some mornings the sky over New York is postcard-blue; other days it wears a grey haze like a bad mood it can't shake. Behind every one of those skies is a number — the **Air Quality Index (AQI)** — and behind every number is a small cascade of consequences: pollutants rising, weather shifting, and somewhere across town, a few more people walking into an ER with a cough that won't quit.

`Air_quality.ipynb` is an investigation into that cascade. It takes a year's worth of daily environmental readings and asks a handful of very human questions:

- Is the air getting better or worse over time — and does it depend on *where* you're standing?
- Does the weather itself let pollution off the hook, or make it worse?
- And — the question that actually matters — does dirtier air put more people in the hospital?

It's a short notebook, but it's built like a magnifying glass: point it at a CSV, and a whole invisible layer of atmosphere snaps into focus.

---

## 🧪 What's Inside the Dataset

The notebook loads `air_quality_analysis.csv` — **1,080 daily records** — and immediately profiles it (`df.info()`, `df.head()`) so nothing about the data's shape is a mystery before the analysis begins.

| Column | What it captures |
|---|---|
| `Date` | The day of observation |
| `Location` | City/monitoring site |
| `AQI` | The headline number — overall Air Quality Index |
| `PM2.5 (ug/m3)` / `PM10 (ug/m3)` | Fine and coarse particulate matter — the stuff that gets into lungs |
| `NO2 (ppb)` / `SO2 (ppb)` / `CO (ppm)` / `O3 (ppb)` | The gaseous pollutant lineup: nitrogen dioxide, sulfur dioxide, carbon monoxide, ozone |
| `Temperature (C)` / `Humidity (%)` / `Wind Speed (km/h)` | The weather context that pollution never exists apart from |
| `Respiratory Hospital Visits` | The human cost — daily count of related hospital visits |

Thirteen columns. One quiet thesis: *air is never just air — it's chemistry, weather, and consequence, all logged on the same day.*

---

## 🔬 The Investigation, Step by Step

### 1. Meet the Data
Before any chart is drawn, the notebook prints a full structural summary and a preview of the first five rows — dtypes, null counts, the works. No plot gets trusted until the table behind it has been read.

### 2. 📈 The AQI Timeline — Watching the Sky Change
A multi-line time series plots **AQI across every location, over the full date range**, each city given its own colored thread. Laid side by side, the lines stop being abstract numbers and start looking like weather itself — spikes, lulls, seasonal drift, one city's air behaving nothing like another's.

### 3. 🌡️ Three Scatterplots, Three Relationships
A single figure, split into three side-by-side lenses:
- **AQI vs. Temperature** — does the air quality index rise and fall with the thermometer?
- **AQI vs. Wind Speed** — does a breezy day actually clear the air, or is that just folklore?
- **AQI vs. Respiratory Hospital Visits** — plotted with a regression line, this is the panel with teeth: it asks directly whether worse air quality tracks with more people needing medical care.

### 4. 🔥 The Correlation Heatmap — Everything, All at Once
The finale zooms out to a full correlation matrix across every numeric column — pollutants, weather, and health outcomes — rendered as a red-blue heatmap with the coefficients annotated in place. It's the moment where every question asked earlier in isolation gets checked against everything else, simultaneously. One glance answers what a dozen individual scatterplots would take forever to show.

---

## 🛠️ Under the Hood

- **Language:** Python 3
- **Libraries:** `pandas` for wrangling, `matplotlib` + `seaborn` for every visual
- **Techniques on display:** time-series line plots with categorical hue, multi-panel scatter/regression figures, and a full Pearson correlation heatmap
- **Runtime:** built and last run in a Colab environment — lightweight enough to execute top to bottom in well under a minute

---

## 🚀 Running It Yourself

```bash
# 1. Set up the environment
pip install pandas matplotlib seaborn

# 2. Make sure the dataset sits next to the notebook
#    (the notebook expects: air_quality_analysis.csv)

# 3. Launch and run all cells
jupyter notebook Air_quality.ipynb
```

Run every cell in order — the notebook is intentionally linear: **load → visualize trends → probe relationships → correlate everything.** Each cell hands the next one a slightly sharper picture of the same story.

---

## 🌍 Why This Kind of Analysis Matters

Air quality data is one of those rare datasets where the abstraction (a three-digit index) and the reality (someone's asthma acting up on a smoggy Tuesday) are never more than one chart away from each other. This notebook doesn't try to be a definitive epidemiological study — it's smaller and more honest than that. It's an exploratory pass, the kind you'd run *before* the real modeling starts, built to answer a simple question well:

**When the air gets worse, what else moves with it?**

The heatmap at the end doesn't just report numbers — it's the closest thing this notebook has to an answer.

---

## 💡 Ideas for Extending It

- Layer in a rolling 7-day average to smooth the AQI timeline and expose seasonal trend lines
- Break the health-outcome regression out **per location**, since pollution's effect on hospital visits may not be uniform across cities
- Bring in a categorical AQI bucket (Good / Moderate / Unhealthy / Hazardous) and compare hospital visit rates *by category* rather than as a continuous regression
- Add a lag analysis — does today's AQI predict *tomorrow's* hospital visits better than same-day?

---

<p align="center"><i>Data tells you what happened. This notebook is just trying to help you notice.</i></p>
