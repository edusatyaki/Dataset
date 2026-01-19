# Google Sheets Logical & Aggregation Functions -- Detailed Guide

This document explains the following functions in detail with syntax,
examples, and use-cases:

IF, AND, OR, NOT, ISBLANK, IFS, COUNTIF, COUNTIFS, SUMIF, SUMIFS,
AVERAGEIF, AVERAGEIFS

------------------------------------------------------------------------

## 1. IF()

### Purpose:

Makes a decision based on a condition.

### Syntax:

=IF(condition, value_if_true, value_if_false)

### Example:

=IF(D2\>=40,"Pass","Fail")

### Explanation:

-   If D2 is 40 or more → returns "Pass"
-   Otherwise → returns "Fail"

### Use Cases:

-   Pass/Fail
-   Eligible/Not Eligible
-   Yes/No classification

------------------------------------------------------------------------

## 2. AND()

### Purpose:

Returns TRUE only if ALL conditions are TRUE.

### Syntax:

=AND(condition1, condition2, ...)

### Example:

=AND(D2\>=85, E2\>=90%)

### Use Case:

Used inside IF for multi-condition rules.

------------------------------------------------------------------------

## 3. OR()

### Purpose:

Returns TRUE if ANY condition is TRUE.

### Syntax:

=OR(condition1, condition2, ...)

### Example:

=OR(D2\>90, E2\>95%)

------------------------------------------------------------------------

## 4. NOT()

### Purpose:

Reverses TRUE to FALSE and FALSE to TRUE.

### Syntax:

=NOT(condition)

### Example:

=NOT(ISBLANK(D2))

------------------------------------------------------------------------

## 5. ISBLANK()

### Purpose:

Checks whether a cell is empty.

### Syntax:

=ISBLANK(cell)

### Example:

=ISBLANK(D2)

------------------------------------------------------------------------

## 6. IFS()

### Purpose:

Cleaner alternative to Nested IF for multiple conditions.

### Syntax:

=IFS(condition1, value1, condition2, value2, ..., TRUE, default_value)

### Example:

=IFS(D2\>=90,"A", D2\>=80,"B", D2\>=70,"C", TRUE,"D")

------------------------------------------------------------------------

## 7. COUNTIF()

### Purpose:

Counts cells that meet ONE condition.

### Syntax:

=COUNTIF(range, criteria)

### Example:

=COUNTIF(D2:D31, "\>80")

------------------------------------------------------------------------

## 8. COUNTIFS()

### Purpose:

Counts cells that meet MULTIPLE conditions (AND logic).

### Syntax:

=COUNTIFS(range1, criteria1, range2, criteria2, ...)

### Example:

=COUNTIFS(D2:D31, "\>80", E2:E31, "\>90%")

------------------------------------------------------------------------

## 9. SUMIF()

### Purpose:

Adds values that meet ONE condition.

### Syntax:

=SUMIF(criteria_range, criteria, sum_range)

### Example:

=SUMIF(C2:C31, "CSE", D2:D31)

------------------------------------------------------------------------

## 10. SUMIFS()

### Purpose:

Adds values that meet MULTIPLE conditions.

### Syntax:

=SUMIFS(sum_range, criteria_range1, criteria1, ...)

### Example:

=SUMIFS(D2:D31, C2:C31, "CSE", D2:D31, "\>70")

------------------------------------------------------------------------

## 11. AVERAGEIF()

### Purpose:

Calculates average for values meeting ONE condition.

### Syntax:

=AVERAGEIF(criteria_range, criteria, average_range)

### Example:

=AVERAGEIF(C2:C31, "CSE", D2:D31)

------------------------------------------------------------------------

## 12. AVERAGEIFS()

### Purpose:

Calculates average for values meeting MULTIPLE conditions.

### Syntax:

=AVERAGEIFS(average_range, criteria_range1, criteria1, ...)

### Example:

=AVERAGEIFS(D2:D31, C2:C31, "CSE", E2:E31, "\>0.80")

------------------------------------------------------------------------




