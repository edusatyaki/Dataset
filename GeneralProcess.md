# Data Analysis Workflow — End-to-End Guide

A structured reference for taking a raw dataset from acquisition through statistical analysis. Use this as a project README template or a teaching handout — each stage lists **what to do, why it matters, common tools (Python-first), and a mini checklist**.

---

## Pipeline at a Glance

```
1. Problem Definition & Dataset Sourcing
        │
2. Data Loading
        │
3. Data Cleaning
        │
4. Data Processing / Feature Engineering
        │
5. Exploratory Data Analysis (EDA)
        │
6. Statistical Analysis
        │
7. Interpretation & Reporting
```

Each stage feeds the next — but in practice it's iterative, not linear. You'll bounce back to Cleaning after EDA reveals a bad column, or back to Loading after realizing you need another table.

---

## Table of Contents

1. [Problem Definition & Dataset Sourcing](#1-problem-definition--dataset-sourcing)
2. [Data Loading](#2-data-loading)
3. [Data Cleaning](#3-data-cleaning)
4. [Data Processing / Feature Engineering](#4-data-processing--feature-engineering)
5. [Exploratory Data Analysis (EDA)](#5-exploratory-data-analysis-eda)
6. [Statistical Analysis](#6-statistical-analysis)
7. [Interpretation & Reporting](#7-interpretation--reporting)
8. [Recommended Project Folder Structure](#8-recommended-project-folder-structure)
9. [Tools & Libraries Cheat Sheet](#9-tools--libraries-cheat-sheet)
10. [Quick Checklist (Print-Friendly)](#10-quick-checklist-print-friendly)

---

## 1. Problem Definition & Dataset Sourcing

Before touching any data, be clear on **what question you're answering**. A dataset without a question leads to aimless analysis.

### What to do
- Write a one-line problem statement (e.g., "Which factors most affect student placement salary?")
- Identify what a "good answer" looks like — a number, a trend, a classification, a recommendation
- List the variables you'd *need* to answer it, even before you have the data
- Source the dataset:
  - **Public repositories**: Kaggle, UCI ML Repository, data.gov.in, Google Dataset Search
  - **APIs**: REST/GraphQL endpoints, official government/company APIs
  - **Web scraping**: BeautifulSoup / Scrapy (check `robots.txt` and licensing first)
  - **Internal/organizational data**: SQL databases, internal Excel/CSV exports, survey tools (Google Forms, Jotform)
  - **Synthetic data**: generated via `faker`, `numpy.random`, or Gen AI, when real data is unavailable or sensitive
- Check licensing, usage rights, and whether the data contains PII
- Do a first-glance profile: file size, number of rows/columns, format (CSV, JSON, SQL, Parquet, Excel)

### Checklist
- [ ] Problem statement written in one sentence
- [ ] Target variable(s) identified
- [ ] Data source documented (URL, date accessed, license)
- [ ] Raw file saved untouched in a `data/raw/` folder (never overwrite raw data)

---

## 2. Data Loading

Getting the data into your working environment correctly, without silently corrupting it.

### What to do
- Choose the right reader for the format:
  - CSV/TSV → `pandas.read_csv()`
  - Excel → `pandas.read_excel()`
  - JSON → `pandas.read_json()` or `json.load()`
  - SQL → `sqlalchemy` + `pandas.read_sql()`
  - Parquet (large data) → `pandas.read_parquet()`
  - APIs → `requests.get()` → parse JSON response
- Immediately inspect:
  - `.shape` — rows × columns
  - `.head()`, `.tail()` — sanity check content
  - `.dtypes` — are numbers stored as numbers, dates as dates?
  - `.info()` — memory usage, non-null counts
  - `.columns` — check for messy column names (spaces, inconsistent casing)
- For large files: read in chunks (`chunksize=`) or use `dask`/`polars` instead of pandas
- Encode correctly — watch for `UnicodeDecodeError`; try `encoding='utf-8'` or `'latin1'`
- Merge multiple sources here if the analysis needs more than one table (`pd.merge`, `pd.concat`)

### Checklist
- [ ] Correct reader/format used, no truncated rows
- [ ] Row/column counts match source expectation
- [ ] Data types initially reviewed
- [ ] Multiple files/tables joined if needed

---

## 3. Data Cleaning

The stage that consumes the most time — and determines whether every later step is trustworthy. **"Garbage in, garbage out"** applies most here.

### What to do

**Missing values**
- Quantify: `df.isnull().sum()`, visualize with a missingness heatmap
- Decide per column: drop, impute (mean/median/mode), forward/backward fill, or model-based imputation (KNNImputer, IterativeImputer)
- Never impute blindly — understand *why* data is missing (random vs. systematic)

**Duplicates**
- `df.duplicated().sum()` → `df.drop_duplicates()`
- Watch for near-duplicates (same entity, slightly different spelling)

**Data types**
- Convert strings that are really numbers, dates, or categories
- Parse dates explicitly: `pd.to_datetime()`, handle multiple formats/timezones

**Outliers**
- Detect via IQR method, Z-score, or visual boxplots
- Decide: remove, cap (winsorize), transform (log), or keep with a flag — depends on whether it's a data error or a genuine extreme value

**Text/categorical cleanup**
- Trim whitespace, standardize case (`str.strip()`, `str.lower()`)
- Fix inconsistent category labels (e.g., "Kolkata", "kolkata", "KOL" → one standard)
- Handle encoding artifacts (mojibake, stray `\xa0` characters)

**Validation**
- Enforce logical constraints (e.g., age can't be negative, percentages must be 0–100)
- Cross-check referential integrity if using multiple joined tables

### Checklist
- [ ] Missing values quantified and handled with a documented strategy
- [ ] Duplicates removed
- [ ] Data types corrected (dates as datetime, numbers as numeric)
- [ ] Outliers identified and a decision made (not ignored)
- [ ] Categorical labels standardized
- [ ] Cleaned data saved separately (`data/processed/`), raw file untouched

---

## 4. Data Processing / Feature Engineering

Shaping clean data into the form your analysis or model actually needs.

### What to do
- **Encoding categorical variables**: one-hot encoding, label encoding, ordinal encoding (choose based on whether the category has order)
- **Scaling/normalization**: StandardScaler (z-score), MinMaxScaler — needed for distance-based methods, not usually for tree-based ones
- **Feature creation**: derive new columns (e.g., `profit = revenue - cost`, `age_group` bucketed from `age`)
- **Binning/discretization**: convert continuous variables into categories when useful for analysis
- **Aggregation**: `groupby()` + `agg()` to summarize at the right granularity (e.g., per-student → per-batch)
- **Reshaping**: `pivot_table()`, `melt()` to switch between wide and long formats
- **Handling imbalance** (for classification tasks): oversampling (SMOTE), undersampling, or class weighting
- **Dimensionality reduction** (if many features): PCA, feature selection based on correlation/importance

### Checklist
- [ ] Categorical variables encoded appropriately for the intended analysis
- [ ] New/derived features documented (what they mean, how computed)
- [ ] Data aggregated to the correct level of granularity
- [ ] Final analysis-ready dataset saved with a clear filename/version

---

## 5. Exploratory Data Analysis (EDA)

Understanding the data's shape, patterns, and relationships *before* forming statistical conclusions. This is where you build intuition.

### What to do

**Univariate analysis** — one variable at a time
- Numerical: histograms, boxplots, `describe()` (mean, median, std, quartiles)
- Categorical: value counts, bar charts, frequency tables

**Bivariate/multivariate analysis** — relationships between variables
- Numerical vs numerical: scatter plots, correlation matrix, heatmap
- Categorical vs numerical: boxplots/violin plots grouped by category
- Categorical vs categorical: cross-tabulation, stacked bar charts

**Pattern & anomaly detection**
- Trends over time (line plots) if data is time-based
- Clusters or groupings (pairplots, PCA-based 2D projection)
- Re-check for outliers now visible only in context of other variables

**Visualization tools**
- `matplotlib` / `seaborn` for static plots
- `plotly` for interactive dashboards
- Keep plots simple and labeled — EDA is for insight, not final presentation polish

### Checklist
- [ ] Summary statistics reviewed for every key variable
- [ ] Distributions visualized (histograms/boxplots)
- [ ] Correlation matrix / heatmap generated
- [ ] Key relationships and anomalies noted in writing, not just eyeballed

---

## 6. Statistical Analysis

Moving from "what does the data look like" to "what can we confidently conclude, and how sure are we?"

### What to do

**Descriptive statistics**
- Mean, median, mode, variance, standard deviation, skewness, kurtosis
- Confirm these against what EDA visuals suggested

**Inferential statistics / hypothesis testing**
- State a null hypothesis (H₀) and alternative (H₁) clearly
- Choose the right test based on data type and question:
  - Compare two group means → **t-test**
  - Compare 3+ group means → **ANOVA**
  - Relationship between categorical variables → **Chi-square test**
  - Relationship between two numeric variables → **Pearson/Spearman correlation**
  - Predict a numeric outcome → **Linear regression**
  - Predict a categorical outcome → **Logistic regression**
- Check test assumptions first (normality via Shapiro-Wilk, equal variance via Levene's test) — using the wrong test invalidates the conclusion
- Report p-value against a pre-chosen significance level (commonly α = 0.05) and interpret in context — never just say "significant," say what it means for the original question

**Confidence intervals & effect sizes**
- Report not just *whether* something is significant but *how large* the effect is
- Confidence intervals give a range of plausible values, more informative than a single p-value

**Regression & modeling (if applicable)**
- Fit the model, check R², coefficients, residual plots
- Validate assumptions: linearity, independence, homoscedasticity, normal residuals

### Checklist
- [ ] Hypotheses explicitly stated before testing
- [ ] Correct test chosen and assumptions verified
- [ ] p-values and effect sizes both reported
- [ ] Conclusions tied back to the original business/research question

---

## 7. Interpretation & Reporting

The step that's easy to skip but is what actually delivers value.

### What to do
- Translate statistical results into plain-language findings a non-technical stakeholder can understand
- Build a narrative: problem → approach → key findings → recommendation
- Create visuals for the *final* audience (polished, not raw EDA plots)
- Package output: dashboard (HTML/Excel/Power BI), report (PDF/DOCX), or presentation (PPTX) depending on audience
- Note limitations and assumptions honestly — no analysis is perfect

### Checklist
- [ ] Findings written in plain language, not just statistical jargon
- [ ] Recommendation or next action clearly stated
- [ ] Limitations/assumptions documented
- [ ] Final deliverable matches the audience (technical report vs. exec summary)

---

## 8. Recommended Project Folder Structure

```
project-name/
├── data/
│   ├── raw/              # original, untouched data
│   ├── processed/        # cleaned & transformed data
│   └── external/         # any reference/lookup data
├── notebooks/
│   ├── 01_data_loading.ipynb
│   ├── 02_cleaning.ipynb
│   ├── 03_eda.ipynb
│   └── 04_statistical_analysis.ipynb
├── src/
│   ├── load_data.py
│   ├── clean_data.py
│   ├── features.py
│   └── stats.py
├── reports/
│   ├── figures/           # exported charts
│   └── final_report.pdf
├── requirements.txt
└── README.md
```

---

## 9. Tools & Libraries Cheat Sheet

| Stage | Python Libraries |
|---|---|
| Dataset Sourcing | `requests`, `beautifulsoup4`, `kaggle` API |
| Data Loading | `pandas`, `sqlalchemy`, `openpyxl`, `dask` |
| Data Cleaning | `pandas`, `numpy`, `missingno` |
| Data Processing | `pandas`, `scikit-learn` (encoders/scalers), `imbalanced-learn` |
| EDA | `matplotlib`, `seaborn`, `plotly`, `pandas-profiling` / `ydata-profiling` |
| Statistical Analysis | `scipy.stats`, `statsmodels`, `scikit-learn` |
| Reporting | `python-docx`, `python-pptx`, `reportlab`, Power BI, Tableau |

---

## 10. Quick Checklist (Print-Friendly)

- [ ] Problem statement defined
- [ ] Dataset sourced and licensing checked
- [ ] Data loaded and shape/types verified
- [ ] Missing values, duplicates, outliers handled
- [ ] Categorical variables encoded, features engineered
- [ ] Univariate + bivariate EDA completed with visuals
- [ ] Hypotheses tested with the correct statistical method
- [ ] Assumptions of each test verified
- [ ] Findings translated into plain-language insights
- [ ] Final report/dashboard delivered with documented limitations

---

*This workflow is intentionally general-purpose — adapt the depth of each stage to the size and stakes of your project. A quick exploratory analysis may skip formal hypothesis testing; a research-grade or placement-facing analysis should not.*
