# Uber Trips Dataset – Spreadsheet Analytics Practice

## Dataset Context

You are provided with an **Uber Trips dataset containing 50,000 records**.  
Each row in the dataset represents a **single Uber trip**.

### Columns in the Dataset
- `trip_id`
- `driver_id`
- `rider_id`
- `city`
- `pickup_lat`, `pickup_lng`
- `drop_lat`, `drop_lng`
- `distance_km`
- `fare_amount`
- `status` (Completed / Cancelled)
- `payment_method` (Cash / UPI / Wallet)
- `pickup_time`
- `drop_time`

---

## Section A: Understanding the Dataset (Recall)

- What does each row in the Uber trips dataset represent?
- Which column uniquely identifies each trip?
- Which columns contain geographical (location) data?
- Which column should be used to analyze revenue?
- Which column helps identify completed vs cancelled trips?
- Which two columns are required to calculate trip duration?
- Which column(s) are categorical and suitable for grouping or aggregation?

---

## Section B: IF Function – Decision Logic

- Create a new column **Trip_Result**:
  - If `status` = `"Completed"`, return `"Successful"`
  - Else, return `"Unsuccessful"`
- Write the IF formula for the above logic.
- What will the output be if `status` = `"Cancelled"`?
- Write an IF formula to classify trips:
  - If `distance_km` > 10 → `"Long Trip"`
  - Else → `"Short Trip"`
- A trip has a distance of 9.8 km. What will the formula return?
- Write a formula to classify fares:
  - Fare ≥ 20 → `"High Fare"`
  - Else → `"Standard Fare"`

---

## Section C: AND / OR Logic (Multi-Condition Decisions)

- Define a **Premium Ride** as:
  - Distance > 15 km **AND**
  - Fare > 30
- Write the formula to identify Premium Rides.
- Will a trip of 18 km and fare 28 be considered Premium? Explain.
- Create a column **Promo_Eligible**:
  - City is **New York OR San Francisco**
  - AND `fare_amount` > 25
- Explain why AND is used outside the OR condition.
- Write a formula to flag **Digital Payments**:
  - Payment method is **UPI OR Wallet**

---

## Section D: NOT & ISBLANK (Data Quality Checks)

- Write a formula to check whether `drop_time` is missing.
- What will the formula return if `drop_time` is blank?
- Why is ISBLANK important in real-world trip datasets?
- Use NOT and ISBLANK to label trips as:
  - `"Valid"` or `"Incomplete"`

---

## Section E: Nested IF / IFS (Multi-Level Classification)

- Create a **Fare Category** column:
  - Fare ≥ 40 → `"Very High"`
  - Fare ≥ 25 → `"High"`
  - Fare ≥ 15 → `"Medium"`
  - Else → `"Low"`
- What category will a fare of 27 fall into?
- Why must the highest condition be checked first in nested IF?
- Rewrite the above logic using the **IFS** function.

---

## Section F: COUNTIF & COUNTIFS (Trip Metrics)

- Count the total number of **Completed** trips.
- Count the number of trips with fare greater than 20.
- Count trips where:
  - City = `"Seattle"`
  - Status = `"Completed"`
- Which function is more appropriate here: COUNTIF or COUNTIFS? Why?
- Count trips paid using **Cash** in **Boston**.

---

## Section G: SUMIF & SUMIFS (Revenue Analysis)

- Calculate total revenue from **Completed trips only**.
- Find the total fare collected in **New York**.
- Calculate total revenue from **San Francisco** trips where distance > 10 km.
- Why is SUMIFS required instead of SUMIF in this case?
- What happens if sum ranges and criteria ranges do not match in size?

---

## Section H: AVERAGEIF & AVERAGEIFS (Performance Analysis)

- Calculate the overall average fare per trip.
- Find the average fare for **Completed trips only**.
- Calculate the average distance traveled in **Seattle**.
- Find the average fare in **Boston** for trips paid via **UPI**.
- Why is AVERAGEIFS important for operational and business analytics?

---

## Section I: Time-Based & Analytical Questions

- Create a column to calculate **Trip Duration (in minutes)** using pickup and drop times.
- Identify trips longer than **30 minutes** using an IF formula.
- Count how many trips lasted more than **20 minutes**.
- Identify which city has the **highest average trip distance**.
- Determine which payment method generates the **highest total revenue**.

---

## Section J: Conditional Formatting (Visualization)

- Highlight fares above 40 using conditional formatting.
- Highlight cancelled trips in red.
- Apply **data bars** to the `distance_km` column. What insight does it provide?
- Apply a **color scale** to `fare_amount`. What patterns can be observed?
- Write a custom conditional formatting rule to highlight **New York** trips.

---

## Section K: Case-Based / Higher-Order Questions

- Why is logical automation essential when analyzing 50,000 trip records?
- How do IF and aggregation functions support Uber’s business decisions?
- Which key metrics would you present to management for **city-wise performance**?
- How would you identify **high-value riders** using this dataset?
- Suggest **three KPIs** Uber can track using this data.

---

### Learning Outcome
By completing these exercises, learners will be able to:
- Apply logical functions (IF, AND, OR, NOT)
- Perform aggregation using COUNTIF, SUMIF, AVERAGEIF
- Analyze large datasets efficiently
- Derive business insights from raw trip-level data
