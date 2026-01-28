## Everlasting Earring Sales Dataset – Column Description Table

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


🟢 LEVEL 1 — EASY (Basics of Pivot Table)
## A. Basic Summaries
Find the total SalesValue for the entire dataset.
Find the total UnitsSold.
Find the total SalesValue by Region.
Find the total SalesValue by Month.
Find the total UnitsSold by ProductType.
Find the total SalesValue by CustomerType (Retail vs Wholesale).
Find the total SalesValue by State.
Find the total SalesValue by City.
Count the number of orders per Region.
Count the number of orders per Month.

## B. Simple Comparisons
Which Region has the highest SalesValue?
Which ProductType sells the most units?
Which Month has the highest SalesValue?
Which CustomerType generates more revenue?
Which State has the highest total sales?

🟡 LEVEL 2 — MEDIUM (Multi-Dimensional Analysis)
## C. Cross Analysis
Show SalesValue by Region and Month.
Show UnitsSold by ProductType and Region.
Show SalesValue by ProductType and CustomerType.
Show SalesValue by State and Month.
Show SalesValue by City and ProductType.
Show SalesValue by SalesRep and Month.
Show UnitsSold by Month and ProductType.
Show SalesValue by Region and CustomerType.
Show SalesValue by ProductType and Month.
Show SalesValue by SalesRep and Region.

## D. Ranking & Filtering
Find the Top 5 Cities by SalesValue.
Find the Top 5 States by SalesValue.
Find the Top 5 SalesReps by SalesValue.
Find the Bottom 5 Cities by SalesValue.
Find the Bottom 3 States by SalesValue.

## E. Averages & Metrics
Find the average UnitsSold per order.
Find the average SalesValue per order.
Find the average SalesValue by ProductType.
Find the average UnitsSold by Region.
Find the average SalesValue by CustomerType.

🔴 LEVEL 3 — HARD (Business & Advanced Pivot Analysis)
## F. Trend & Growth Analysis
Show month-wise SalesValue trend for each Region.
Identify which Region shows the highest growth from Jan to Jun.
Identify which ProductType is growing fastest month-over-month.
Which Month shows overall highest growth compared to previous month?
Show SalesRep performance trend over time.

## G. Contribution & Share Analysis
Find % contribution of each Region to total SalesValue.
Find % contribution of each ProductType to total SalesValue.
Find % contribution of each Month to total SalesValue.
Find ProductType mix % inside each Region.
Find CustomerType mix % inside each ProductType.

## H. Performance & Efficiency
Which SalesRep has the highest average SalesValue per order?
Which City has the highest average order value?
Which State has the highest sales consistency across months?
Which Region has the highest average SalesValue per order?
Which ProductType has the highest revenue per unit sold?

## I. Advanced Business Questions
If management wants to focus only on top 20% revenue-generating cities, which cities should be selected?
Which 5 SalesReps should get incentives based on performance?
Which Region should get more marketing budget and why?
Which ProductType should be promoted more and why?
Which States are underperforming compared to their Region average?

## BONUS — SQL / Data Engineering Style Questions
Write a query / pivot to find duplicate cities across states.
Create a report showing only Retail customers in South Region.
Find months where sales dropped compared to previous month.
Find cities where Drop Earrings sell more than Stud Earrings.
Find regions where Wholesale contributes more than 50% revenue.

🏆 FINAL EXAM / CAPSTONE QUESTIONS
Build a complete management dashboard showing:
Region-wise performance
Product-wise performance
Monthly trend
Top & Bottom performers
Give 3 business recommendations based on the data.
Identify risk areas and growth opportunities.
