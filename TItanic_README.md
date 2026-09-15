# 🚢 Titanic Dataset — Exploratory Data Analysis

<p align="center">
  <img src="images/notebook_output_1.png" alt="Actual Titanic notebook visualization" width="100%">
</p>

<p align="center">
  <b>Exploratory Data Analysis of the Titanic Dataset using Python, Pandas, Matplotlib and Seaborn</b>
</p>

---

## 👨‍🎓 Student Information

| Detail | Information |
|---|---|
| **Student Name** | **Sumit Kaswala** |
| **Course** | **Data Analysis** |
| **Academic Level** | **B.Tech Final Year** |
| **Instructor** | **Girish Gondaliya** |
| **Project File** | `titanic.ipynb` |
| **Dataset File** | `titanic.csv` |
| **Project Type** | Exploratory Data Analysis (EDA) |

---

## 📌 Project Overview

This project performs Exploratory Data Analysis (EDA) on the Titanic dataset.

The notebook uses Python libraries such as **Pandas, Matplotlib and Seaborn** to inspect the dataset, identify missing values, clean the Age feature, study passenger survival patterns and visualize relationships between important variables.

The analysis mainly focuses on:

- Dataset structure and information
- Missing values
- Cleaning missing Age values
- Survival rate by gender
- Survival rate by passenger class
- Survival rate by class and gender
- Age distribution by survival status
- Numerical feature correlation

The project is presented in a simple and practical format suitable for a **B.Tech Data Analysis course**.

---

# 🎯 Objectives

The main objectives of this project are:

1. Load the Titanic dataset into a Pandas DataFrame.
2. Understand the structure of the dataset.
3. Identify missing values.
4. Handle missing values in the `Age` column.
5. Compare survival rates between male and female passengers.
6. Compare survival rates between passenger classes.
7. Study survival using both passenger class and gender.
8. Visualize the age distribution according to survival status.
9. Calculate and visualize correlations between numerical features.
10. Understand how visualization helps in exploratory data analysis.

---

# 🧰 Technologies Used

### 🐍 Python
The complete notebook is written in Python.

### 🐼 Pandas
Used for:

- Reading the CSV dataset
- Creating and manipulating the DataFrame
- Inspecting data
- Checking missing values
- Filling missing Age values
- Selecting numerical columns

### 📊 Matplotlib
Used for:

- Creating figures
- Creating multiple plots
- Setting titles and labels
- Displaying visualizations

### 🎨 Seaborn
Used for:

- Bar plots
- KDE plots
- Correlation heatmap
- Improving the visual appearance of graphs

---

# 📦 Libraries

The notebook imports:

```python
import matplotlib.pyplot as plt
import pandas as pd
import seaborn as sns
```

It also applies the Seaborn theme:

```python
sns.set_theme(style="whitegrid")
```

---

# 📁 Project Structure

```text
Titanic-EDA/
│
├── titanic.ipynb
├── titanic.csv
├── README.md
│
└── images/
    └── notebook_output_1.png
```

The image in this README is stored **locally inside the project**, so it is not an external image link.

---

# 🔄 Data Analysis Workflow

```text
             ┌──────────────────┐
             │   Titanic CSV    │
             └────────┬─────────┘
                      ↓
             ┌──────────────────┐
             │ Load using Pandas│
             └────────┬─────────┘
                      ↓
             ┌──────────────────┐
             │ Dataset Inspection│
             └────────┬─────────┘
                      ↓
             ┌──────────────────┐
             │ Missing Values   │
             └────────┬─────────┘
                      ↓
             ┌──────────────────┐
             │ Age Cleaning     │
             └────────┬─────────┘
                      ↓
             ┌──────────────────┐
             │ Survival Analysis│
             └────────┬─────────┘
                      ↓
             ┌──────────────────┐
             │ Visualization    │
             └────────┬─────────┘
                      ↓
             ┌──────────────────┐
             │ Correlation      │
             └──────────────────┘
```

---

# 🔍 Step 1 — Loading the Dataset

The notebook loads the Titanic CSV file using:

```python
df = pd.read_csv("titanic.csv")
```

The dataset is stored in the DataFrame:

```python
df
```

The notebook therefore expects the dataset file to be available with the exact name:

```text
titanic.csv
```

---

# 🔎 Step 2 — Dataset Inspection

The notebook checks the structure of the DataFrame using:

```python
print(df.info())
```

The actual notebook output shows:

- **891 entries**
- **12 columns**
- Integer, floating-point and object data types
- `Age` has **714 non-null values**
- `Cabin` has **204 non-null values**
- `Embarked` has **889 non-null values**

The complete dataset contains these columns:

| Column | Description |
|---|---|
| `PassengerId` | Passenger identification number |
| `Survived` | Survival status |
| `Pclass` | Passenger class |
| `Name` | Passenger name |
| `Sex` | Passenger gender |
| `Age` | Passenger age |
| `SibSp` | Number of siblings/spouses aboard |
| `Parch` | Number of parents/children aboard |
| `Ticket` | Ticket information |
| `Fare` | Passenger fare |
| `Cabin` | Cabin information |
| `Embarked` | Port of embarkation |

---

# 🧹 Step 3 — Missing Value Analysis

The notebook uses:

```python
print(df.isnull().sum())
```

The actual output identifies the following missing values:

| Column | Missing Values |
|---|---:|
| `PassengerId` | 0 |
| `Survived` | 0 |
| `Pclass` | 0 |
| `Name` | 0 |
| `Sex` | 0 |
| `Age` | 177 |
| `SibSp` | 0 |
| `Parch` | 0 |
| `Ticket` | 0 |
| `Fare` | 0 |
| `Cabin` | 687 |
| `Embarked` | 2 |

This step is important because missing data can affect analysis and visualization.

---

# 🛠️ Step 4 — Cleaning the Age Column

The notebook creates a cleaned Age column:

```python
df["Age_Cleaned"] = df["Age"].fillna(df["Age"].median())
```

The original `Age` column is not overwritten.

Instead, a new feature called:

```text
Age_Cleaned
```

is created.

Missing Age values are replaced using the **median Age**.

This cleaned column is then used for the age distribution visualization.

---

# 📊 Step 5 — Survival Rate by Gender

The notebook creates a bar plot using:

```python
sns.barplot(
    data=df,
    x="Sex",
    y="Survived",
    ...
)
```

The resulting graph is titled:

**Survival Rate by Gender**

This visualization compares the average `Survived` value for the gender categories.

Because `Survived` is represented numerically, its mean can be interpreted as the proportion of passengers who survived within each group.

---

# 🛳️ Step 6 — Survival Rate by Passenger Class

The notebook creates another bar plot:

```python
sns.barplot(
    data=df,
    x="Pclass",
    y="Survived",
    ...
)
```

The graph is titled:

**Survival Rate by Passenger Class**

This allows the survival outcome to be compared across:

- 1st Class
- 2nd Class
- 3rd Class

---

# 👥 Step 7 — Survival Rate by Class & Gender

The notebook combines passenger class and gender:

```python
sns.barplot(
    data=df,
    x="Pclass",
    y="Survived",
    hue="Sex",
    ...
)
```

The resulting graph is titled:

**Survival Rate by Class & Gender**

This provides a more detailed view than analyzing class or gender separately.

It allows us to observe the survival pattern for different gender groups within each passenger class.

---

# 🎂 Step 8 — Age Distribution by Survival Status

The notebook creates a KDE plot:

```python
sns.kdeplot(
    data=df,
    x="Age_Cleaned",
    hue="Survived",
    common_norm=False,
    fill=True,
    alpha=0.5,
    palette="Set1",
)
```

The graph is titled:

**Age Distribution by Survival Status**

The visualization compares the distribution of cleaned passenger ages according to whether the passenger survived.

---

# 🔥 Step 9 — Correlation Matrix

The notebook selects numerical columns using:

```python
numeric_cols = df.select_dtypes(
    include=["float64", "int64"]
).drop(columns=["PassengerId"])
```

`PassengerId` is removed because it is an identifier rather than a meaningful numerical measurement for correlation analysis.

The correlation matrix is then visualized with:

```python
sns.heatmap(
    numeric_cols.corr(),
    annot=True,
    cmap="coolwarm",
    fmt=".2f",
    linewidths=0.5
)
```

The resulting visualization is titled:

**Numerical Feature Correlation Matrix**

---

# 🖼️ Actual Notebook Visualization

The following image is **not a placeholder**. It is the actual PNG visualization embedded in the uploaded `titanic.ipynb` notebook output.

<p align="center">
  <img src="images/notebook_output_1.png" alt="Actual output from Titanic notebook" width="100%">
</p>

---

# 📈 Visualization Explanation

The notebook's main visualization combines three survival comparisons into one figure:

### 1. Survival Rate by Gender
Shows the difference in average survival outcome between the gender groups.

### 2. Survival Rate by Passenger Class
Shows how the average survival outcome varies across passenger classes.

### 3. Survival Rate by Class & Gender
Shows the combined relationship between passenger class and gender.

The notebook then separately generates:

- Age distribution visualization
- Numerical correlation heatmap

---

# 🧠 Important Data Analysis Concepts

This project demonstrates the following concepts:

| Concept | Implementation |
|---|---|
| Data loading | `pd.read_csv()` |
| DataFrame | `df` |
| Data inspection | `df.info()` |
| Missing-value detection | `df.isnull().sum()` |
| Median calculation | `df["Age"].median()` |
| Missing-value handling | `fillna()` |
| Feature creation | `Age_Cleaned` |
| Categorical analysis | `Sex`, `Pclass` |
| Bar plot | `sns.barplot()` |
| KDE plot | `sns.kdeplot()` |
| Correlation | `.corr()` |
| Heatmap | `sns.heatmap()` |

---

# 💡 What This Project Demonstrates

This project shows a basic but complete Exploratory Data Analysis process.

The important idea is to first understand the data before trying to build a machine-learning model.

The workflow demonstrates:

**Load → Inspect → Clean → Analyze → Visualize → Understand**

---

# ▶️ How to Run the Project

## Method 1 — Google Colab

### Step 1
Open Google Colab.

### Step 2
Upload:

```text
titanic.ipynb
```

### Step 3
Upload:

```text
titanic.csv
```

### Step 4
Make sure both files are accessible in the same Colab working environment.

### Step 5
Run the notebook cells from top to bottom.

---

## Method 2 — Jupyter Notebook

Install the required libraries:

```bash
pip install pandas matplotlib seaborn jupyter
```

Start Jupyter:

```bash
jupyter notebook
```

Open:

```text
titanic.ipynb
```

Run the cells using:

```text
Shift + Enter
```

---

# ⚠️ Dataset Requirement

The notebook contains:

```python
df = pd.read_csv("titanic.csv")
```

Therefore, the dataset must be available as:

```text
titanic.csv
```

If the CSV is not present, the notebook will not be able to load the data.

---

# 🚀 Future Improvements

The current notebook is focused on Exploratory Data Analysis.

It could be extended with:

- More categorical feature analysis
- Fare analysis
- Family-size analysis
- Embarkation analysis
- Additional statistical analysis
- Feature engineering
- Categorical encoding
- Logistic Regression
- Decision Tree
- Random Forest
- Model accuracy comparison
- Confusion matrix
- Classification report
- Interactive dashboards

These are suggested extensions and are not claimed as part of the current notebook.

---

# 🏆 Project Highlights

✨ Beginner-friendly Data Analysis project

🐍 Python-based implementation

🐼 Pandas data handling

📊 Matplotlib visualization

🎨 Seaborn visualization

🧹 Missing-value handling

👥 Gender-based analysis

🛳️ Passenger-class analysis

🎂 Age-distribution analysis

🔥 Correlation analysis

📓 Jupyter/Google Colab compatible

---

# 📚 Learning Outcomes

After completing this project, a student can understand:

1. How to load a CSV file using Pandas.
2. How to inspect a DataFrame.
3. How to identify missing data.
4. How to handle missing numerical values using a median.
5. How to create a new cleaned feature.
6. How to compare categorical groups.
7. How to create bar plots.
8. How to create KDE distribution plots.
9. How to calculate correlations.
10. How to create a correlation heatmap.
11. How to present data-analysis results visually.

---

# 🎓 Academic Information

This project is prepared as part of **Data Analysis practical/project work** for:

**B.Tech Final Year**

### Student
**Sumit Kaswala**

### Instructor
**Girish Gondaliya**

---

# ✅ Conclusion

The Titanic dataset provides a useful real-world example for learning Exploratory Data Analysis.

In this project, the dataset is loaded with Pandas, inspected for structure and missing values, and the missing Age values are handled using the median. The notebook then explores survival patterns using gender and passenger class, studies age distribution by survival status, and examines relationships between numerical features through a correlation heatmap.

The project demonstrates an important Data Analysis principle:

> **Understand the data first, clean it carefully, visualize it clearly, and then interpret the patterns.**

---

<p align="center">
  <b>🚢 Titanic EDA | Python | Pandas | Matplotlib | Seaborn</b>
</p>

<p align="center">
  <i>Created for B.Tech Final Year — Data Analysis</i>
</p>
