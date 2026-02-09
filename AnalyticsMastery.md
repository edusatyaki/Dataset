# Analytics Mastery  
### Array Formulas & What-If Analysis

A practical guide to mastering Google Sheets automation and analytical thinking using dynamic formulas and decision-analysis tools.

---

## 1. Google Sheets Dynamic Functions
**Category:** Automation

Dynamic functions allow automatic expansion and processing of entire datasets without copying formulas.

| Function | Syntax | Example | Explanation |
|-----------|--------|---------|-------------|
| **ARRAYFORMULA** | `=ARRAYFORMULA(range_formula)` | `=ARRAYFORMULA(D2:D * E2:E)` | Processes an entire column with one formula and expands automatically for new data. |
| **FILTER** | `=FILTER(range, condition)` | `=FILTER(A2:K, I2:I > 50000)` | Extracts rows that meet a condition without altering the original dataset. |
| **UNIQUE** | `=UNIQUE(range)` | `=UNIQUE(B2:B)` | Removes duplicate entries to create clean lists. |
| **SORTN** | `=SORTN(range, n, 0, col, FALSE)` | `=SORTN(A2:K, 10, 0, 11, FALSE)` | Returns Top N results, such as top profitable sales. |
| **QUERY** | `=QUERY(data, query)` | `"select F, sum(K) group by F"` | Acts like SQL inside Sheets for advanced reporting. |

---

## 2. Conditional Summaries & Logic
**Category:** Insights

Used to summarize and categorize data automatically.

| Function | Syntax | Example | Explanation |
|-----------|--------|---------|-------------|
| **SUMIF** | `=SUMIF(range, criteria, sum_range)` | `=SUMIF(F2:F, "North", K2:K)` | Adds values matching a category. |
| **COUNTIF** | `=COUNTIF(range, criteria)` | `=COUNTIF(L2:L, "High Profit")` | Counts entries meeting a rule. |
| **IF (Array Logic)** | `=IF(logical, true, false)` | `=IF(K2:K > 10000, "High", "Low")` | Categorizes rows automatically. |

---

## 3. What-If Analysis Tools
**Category:** Strategy

Commonly used in LibreOffice Calc or spreadsheet tools for prediction and planning.

| Tool | Logic Direction | Primary Use Case |
|------|-----------------|------------------|
| **Scenario Manager** | Inputs → Result | Compare business cases such as Best, Worst, or Normal conditions. |
| **Goal Seek** | Result → Input | Find required price, sales, or quantity to achieve a profit target. |

---

## Learning Context
**Project:** Radha's Junior Data Analyst Journey  
**Year:** 2026 Analytics Dashboard
