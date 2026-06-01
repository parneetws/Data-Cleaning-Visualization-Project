# Titanic Data Cleaning & Visualization

A Python project that cleans and explores the Titanic dataset — handling missing values, outliers, and duplicates, then visualizing key findings in a dashboard.

-----

## Dataset

**Titanic passenger data** — 891 rows, 12 columns.

Loaded directly from URL (no manual download needed):

```
https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv
```

Columns: `Survived`, `Pclass`, `Name`, `Sex`, `Age`, `SibSp`, `Parch`, `Ticket`, `Fare`, `Cabin`, `Embarked`

-----

## Setup

**Requirements:** Python 3.7+

Install dependencies:

```bash
pip install pandas numpy matplotlib seaborn
```

Run the script:

```bash
python data_analysis.py
```

-----

## What the Script Does

### 1. Data Exploration

- Prints shape, first few rows, data types
- Shows missing value counts per column

### 2. Handling Missing Values

- **Age** — filled with median grouped by `Pclass` + `Sex` (more accurate than a single global median)
- **Embarked** — only 2 missing, filled with mode
- **Cabin** — dropped (~77% missing, not useful)

### 3. Removing Duplicates

- Checks for and removes any duplicate rows

### 4. Outlier Handling

- Uses the **IQR method** on `Age` and `Fare`
- Outliers are capped (not dropped) to preserve data

### 5. Feature Engineering

|New Column   |Description                               |
|-------------|------------------------------------------|
|`family_size`|SibSp + Parch + 1                         |
|`alone`      |1 if travelling solo, else 0              |
|`age_group`  |Child / Teen / Adult / Middle-age / Senior|

### 6. Visualizations (3×3 dashboard)

1. Survival count (bar)
1. Survival rate by passenger class
1. Survival rate by sex
1. Age distribution by survival (overlapping histogram)
1. Fare distribution by class (boxplot)
1. Survival rate by age group
1. Survival rate by family size (line)
1. Survival rate by embarkation point
1. Correlation heatmap

Dashboard is saved as **`titanic_dashboard.png`** in the same folder.

-----

## Key Findings

- Overall survival rate was around **38%**
- **Women survived at ~74%** vs men at ~19%
- **1st class passengers** had the highest survival rate (~63%)
- Travelling with **2–4 family members** improved survival odds
- **Children** had a relatively higher survival rate than adults

-----

## Files

```
├── data_analysis.py       # main script
├── titanic_dashboard.png  # output dashboard (generated on run)
└── README.md              # this file
```