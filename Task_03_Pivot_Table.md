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
