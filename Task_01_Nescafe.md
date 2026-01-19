# Nescafe Dataset – Spreadsheet & Data Analysis Practice

## Dataset Context

You are provided with a **Nescafe sales dataset** containing sales, customer, product, and marketing information for a beverage business operating across multiple markets and regions.

This dataset is suitable for practicing:
- Data cleaning
- Text and date functions
- Logical checks
- Aggregation and reporting
- Business performance analysis  
using **Excel, Google Sheets, SQL, or Python**.

**Dataset Link:**  
https://github.com/edusatyaki/Dataset/blob/main/Nescafe.csv

---

## Dataset Columns

| Column Name | Description |
|------------|-------------|
| Area Code | Telephone area code representing the customer’s region |
| Date | Numeric date value representing the transaction period |
| Market | Business market region where the sale occurred |
| Market Size | Market classification (Major / Small Market) |
| Product | Name of the product sold |
| Product Line | Product category (Beans, Leaves, etc.) |
| Product Type | Beverage type (Coffee, Tea, Espresso) |
| State | State where the sale occurred |
| Type | Product variant (Regular / Decaf) |
| Budget COGS | Planned cost of goods sold |
| Budget Margin | Planned profit margin |
| Budget Profit | Planned profit |
| Budget Sales | Planned sales |
| COGS | Actual cost of goods sold |
| Inventory | Quantity of stock available |
| Margin | Actual profit margin |
| Marketing | Marketing expense |
| Profit | Actual profit |
| Sales | Actual sales revenue |
| Total Expenses | Total cost including COGS and marketing |
| Order Date | Date when the order was placed |
| Customer Name | Name of the customer |
| City | Customer city |
| Promo Code | Promotional code used (if any) |
| Full Product | Complete product description |

---

## Section A: Data Cleaning & Text Functions

- Check whether the **Promo Code** column is blank.
- Remove **non-printable characters** from `Customer Name`.
- Remove **extra leading and trailing spaces** from `Customer Name`.
- Replace spaces in `Customer Name` with **hyphens (-)**.
- Count the number of characters in the `Product` name.
- Convert `Customer Name` into **Proper Case**.
- Convert `City` to **UPPERCASE**.
- Convert `City` to **lowercase**.

---

## Section B: Date & Time Functions

- Display `Order Date` in **DD-MMM-YYYY** format.
- Display **today’s date**.
- Display **current date and time**.
- Extract **Year** from `Order Date`.
- Extract **Month** from `Order Date`.
- Extract **Day** from `Order Date`.
- Find the **day of the week** from `Order Date`.
- Calculate the **number of days between Order Date and today**.
- Find the **last day of the month** for `Order Date`.

---

## Section C: Data Transformation & Combination

- Combine `Product Line` and `Product` into a single column.
- Combine `City`, `State`, and `Market` into one column separated by commas.
- Create a readable **Full Location** field using City, State, and Market.

---

## Section D: Logical Checks

- Identify rows where `Promo Code` is missing.
- Count how many rows have `Promo Code = "SAVE10"`.
- Count how many rows have **blank Promo Codes**.

---

## Section E: Aggregation & Business Analysis

- Find the **total Sales** where `Product Type` is **Coffee**.
- Calculate the **average Profit** where `Market` is **Central**.
- Count total number of sales records per **Market**.
- Compare **Budget Sales vs Actual Sales**.
- Identify products with **negative Profit**.

---

## Section F: Business Insight Questions

- Which **Product Type** generates the highest sales?
- Which **Market** is the most profitable?
- Which cities contribute the most to overall revenue?
- How effective are Promo Codes in driving sales?
- Is there a gap between **Budget Profit** and **Actual Profit**?

---

## Learning Outcomes

By completing these tasks, learners will be able to:
- Clean and standardize textual data
- Work with date and time functions
- Apply logical and conditional checks
- Perform aggregations for business reporting
- Derive actionable insights from sales data

---

### Suggested Tools
- Excel / Google Sheets
- SQL (optional extension)
- Python (Pandas)

