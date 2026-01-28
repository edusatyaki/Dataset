# Everlasting Earring Sales Analytics Project
### Pivot Table, Excel & Data Analytics Practice Case Study

---

## 📁 Dataset Overview

This project uses a sales dataset of the **Everlasting** brand earrings across different regions of India.

The dataset contains **300+ transaction records** with the following fields:

- OrderID, Region, State, City, Month  
- SalesRep, ProductType, UnitsSold, UnitPrice  
- SalesValue, CustomerType  

> Each row represents **one sales transaction**.

---

# Dataset Column Description

## Detailed Column Dictionary

| Column Name  | Data Type           | What it Represents                                          | Why It Is Important                                 | Example Use in Pivot / Analysis         |
| ------------ | ------------------- | ----------------------------------------------------------- | --------------------------------------------------- | --------------------------------------- |
| OrderID      | Identifier (Number) | Unique number for each sales transaction                    | Used to count orders and track individual records   | Count of orders per region or per month |
| Region       | Text (Category)     | Major geographical zone of India (North, South, East, West) | Used for high-level geographic performance analysis | Total sales by Region                   |
| State        | Text (Category)     | State where the sale occurred                               | Helps in state-level performance tracking           | State-wise revenue                      |
| City         | Text (Category)     | City where the sale happened                                | Helps identify top and weak markets                 | Top 5 cities by sales                   |
| Month        | Time Period         | Month in which the sale occurred (Jan–Jun 2025)             | Used for trend and growth analysis                  | Month-wise sales trend                  |
| SalesRep     | Text (Category)     | Sales executive who made the sale                           | Used to measure employee performance                | Top SalesRep by revenue                 |
| ProductType  | Text (Category)     | Type of earring sold (Stud / Hoop / Drop)                   | Used for product performance and mix analysis       | Product-wise revenue share              |
| UnitsSold    | Number (Integer)    | Quantity of earrings sold in that order                     | Measures sales volume                               | Total units sold by product             |
| UnitPrice    | Number (Currency)   | Price of one unit of product                                | Used to calculate revenue and pricing analysis      | Average selling price                   |
| SalesValue   | Number (Currency)   | Total revenue of the order (UnitsSold × UnitPrice)          | Most important business metric – total sales        | Total revenue by any dimension          |
| CustomerType | Text (Category)     | Type of customer (Retail / Wholesale)                       | Used for customer segmentation analysis             | Retail vs Wholesale revenue             |

---

## Short Version (For Quick Revision)

| Column              | Type      | Role                   |
| ------------------- | --------- | ---------------------- |
| OrderID             | ID        | Transaction identifier |
| Region, State, City | Dimension | Geography analysis     |
| Month               | Time      | Trend analysis         |
| SalesRep            | Dimension | Performance analysis   |
| ProductType         | Dimension | Product analysis       |
| CustomerType        | Dimension | Customer segmentation  |
| UnitsSold           | Measure   | Volume                 |
| UnitPrice           | Measure   | Price                  |
| SalesValue          | Measure   | Revenue                |

---
## Sample Dataset

| OrderID | Region | State         | City       | Month    | SalesRep     | ProductType   | UnitsSold | UnitPrice | SalesValue | CustomerType |
| ------: | ------ | ------------- | ---------- | -------- | ------------ | ------------- | --------- | --------- | ---------- | ------------ |
|   10001 | North  | Delhi         | Delhi      | Jun-2025 | Meera Patel  | Stud Earrings | 19        | 500       | 9500       | Retail       |
|   10002 | North  | Himachal      | Shimla     | Jan-2025 | Aditya Sen   | Hoop Earrings | 7         | 850       | 5950       | Retail       |
|   10003 | North  | Haryana       | Sonipat    | Feb-2025 | Tara Chauhan | Drop Earrings | 6         | 950       | 5700       | Retail       |
|   10004 | West   | Maharashtra   | Pune       | Apr-2025 | Aditya Sen   | Hoop Earrings | 5         | 850       | 4250       | Retail       |
|   10005 | West   | Gujarat       | Ahmedabad  | Mar-2025 | Saurav Roy   | Stud Earrings | 26        | 500       | 13000      | Retail       |
|   10006 | North  | Uttar Pradesh | Lucknow    | Jan-2025 | Arjun Nair   | Hoop Earrings | 21        | 850       | 17850      | Retail       |
|   10007 | West   | Goa           | Panaji     | Jan-2025 | Divya Singh  | Stud Earrings | 40        | 500       | 20000      | Wholesale    |
|   10008 | East   | Jharkhand     | Jamshedpur | Feb-2025 | Rahul Singh  | Stud Earrings | 19        | 500       | 9500       | Wholesale    |
|   10009 | North  | Haryana       | Sonipat    | Jan-2025 | Divya Singh  | Hoop Earrings | 34        | 850       | 28900      | Wholesale    |

---
# LEVEL 1 — EASY (Basics of Pivot Table)

## A. Basic Summaries

1. Find the total **SalesValue** for the entire dataset  
2. Find the total **UnitsSold**  
3. Find the total **SalesValue by Region**  
4. Find the total **SalesValue by Month**  
5. Find the total **UnitsSold by ProductType**  
6. Find the total **SalesValue by CustomerType**  
7. Find the total **SalesValue by State**  
8. Find the total **SalesValue by City**  
9. Count the **number of orders per Region**  
10. Count the **number of orders per Month**

---

## B. Simple Comparisons

11. Which **Region** has the highest SalesValue?  
12. Which **ProductType** sells the most units?  
13. Which **Month** has the highest SalesValue?  
14. Which **CustomerType** generates more revenue?  
15. Which **State** has the highest total sales?

---

# LEVEL 2 — MEDIUM (Multi-Dimensional Analysis)

## C. Cross Analysis

16. SalesValue by Region and Month  
17. UnitsSold by ProductType and Region  
18. SalesValue by ProductType and CustomerType  
19. SalesValue by State and Month  
20. SalesValue by City and ProductType  
21. SalesValue by SalesRep and Month  
22. UnitsSold by Month and ProductType  
23. SalesValue by Region and CustomerType  
24. SalesValue by ProductType and Month  
25. SalesValue by SalesRep and Region  

---

## D. Ranking & Filtering

26. Top 5 Cities by SalesValue  
27. Top 5 States by SalesValue  
28. Top 5 SalesReps by SalesValue  
29. Bottom 5 Cities by SalesValue  
30. Bottom 3 States by SalesValue  

---

## E. Averages & Metrics

31. Average UnitsSold per order  
32. Average SalesValue per order  
33. Average SalesValue by ProductType  
34. Average UnitsSold by Region  
35. Average SalesValue by CustomerType  

---

# LEVEL 3 — HARD (Business & Advanced Pivot Analysis)

## F. Trend & Growth Analysis

36. Month-wise SalesValue trend for each Region  
37. Region with highest growth from Jan to Jun  
38. Fastest growing ProductType month-over-month  
39. Month with highest growth compared to previous month  
40. SalesRep performance trend over time  

---

## G. Contribution & Share Analysis

41. % contribution of each Region  
42. % contribution of each ProductType  
43. % contribution of each Month  
44. ProductType mix % inside each Region  
45. CustomerType mix % inside each ProductType  

---

## H. Performance & Efficiency

46. SalesRep with highest average order value  
47. City with highest average order value  
48. State with most consistent sales  
49. Region with highest average order value  
50. ProductType with highest revenue per unit  

---

## I. Advanced Business Questions

51. Top 20% revenue-generating cities  
52. Top 5 SalesReps for incentives  
53. Which Region deserves more marketing budget and why  
54. Which ProductType should be promoted more and why  
55. Which States are underperforming vs Region average  

---

# BONUS — SQL / Data Engineering Style

56. Find duplicate cities across states  
57. Report of Retail customers in South Region  
58. Months where sales dropped  
59. Cities where Drop > Stud sales  
60. Regions where Wholesale > 50% revenue  

---

# FINAL CAPSTONE PROJECT

## Build a Management Dashboard Showing:

- Region-wise performance  
- Product-wise performance  
- Monthly trend  
- Top & Bottom performers  

---

## Business Case Study

61. Give **3 business recommendations**  
62. Identify **risk areas & growth opportunities**

---

# Learning Outcomes

- Pivot Tables (Beginner → Advanced)  
- Business KPI analysis  
- Trend & growth analysis  
- Decision making using data  
- Real-world analytics project experience  

---

