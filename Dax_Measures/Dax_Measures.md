# 📊 DAX Measures Documentation

This document contains the primary DAX measures used in the **AdventureWorks 360 – Enterprise Business Intelligence Platform**.

---

# 💰 Sales Measures

## Total Sales

```DAX
Total Sales =
SUM('Sales Data'[SalesAmount ($)])
```

Returns the total sales generated across all transactions.

---

## Total Orders

```DAX
Total Orders =
DISTINCTCOUNT('Sales Data'[SalesOrderNumber])
```

Returns the total number of unique sales orders.

---

## Average Order Value

```DAX
Average Order Value =
DIVIDE(
    [Total Sales],
    [Total Orders],
    0
)
```

Calculates the average revenue generated per order.

---

# 📈 Profit Measures

## Total Profit

```DAX
Total Profit =
SUM('Sales Data'[Profit ($)])
```

Returns total business profit.

---

## Total Cost

```DAX
Total Cost =
SUM('Sales Data'[TotalProductCost])
```

Calculates total product cost.

---

## Profit Margin %

```DAX
Profit Margin % =
DIVIDE(
    [Total Profit],
    [Total Sales],
    0
)
```

Measures profitability as a percentage of total sales.

---

## ROI

```DAX
ROI =
DIVIDE(
    [Total Profit],
    [Total Cost],
    0
)
```

Calculates Return on Investment.

---

# 👥 Customer Measures

## Total Customers

```DAX
Total Customers =
DISTINCTCOUNT('Sales Data'[CustomerKey])
```

Returns the number of unique customers.

---

## Revenue per Customer

```DAX
Revenue per Customer =
DIVIDE(
    [Total Sales],
    [Total Customers],
    0
)
```

Calculates average revenue generated from each customer.

---

# 📦 Product Measures

## Quantity Sold

```DAX
Quantity Sold =
SUM('Sales Data'[OrderQuantity])
```

Returns total units sold.

---

## Average Selling Price

```DAX
Average Selling Price =
DIVIDE(
    [Total Sales],
    [Quantity Sold],
    0
)
```

Calculates average selling price per unit.

---

# 🌍 Geographic Measures

## Sales by Territory

```DAX
Sales by Territory =
[Total Sales]
```

Used for regional performance analysis.

---

## Profit by Territory

```DAX
Profit by Territory =
[Total Profit]
```

Used for profitability comparison across territories.

---

# 📅 Time Intelligence Measures

## Previous Year Sales

```DAX
Previous Year Sales =
CALCULATE(
    [Total Sales],
    SAMEPERIODLASTYEAR('Calendar'[Date])
)
```

Returns sales for the same period in the previous year.

---

## YoY Growth %

```DAX
YoY Growth % =
DIVIDE(
    [Total Sales] - [Previous Year Sales],
    [Previous Year Sales],
    0
)
```

Calculates Year-over-Year sales growth.

---

## Running Total Sales

```DAX
Running Total Sales =
CALCULATE(
    [Total Sales],
    FILTER(
        ALL('Calendar'),
        'Calendar'[Date] <= MAX('Calendar'[Date])
    )
)
```

Displays cumulative sales over time.

---

# 🏆 Ranking Measures

## Product Rank

```DAX
Product Rank =
RANKX(
    ALL('Sales Data'[ProductName]),
    [Total Sales],
    ,
    DESC
)
```

Ranks products based on sales.

---

## Customer Rank

```DAX
Customer Rank =
RANKX(
    ALL('Sales Data'[CustomerName]),
    [Total Sales],
    ,
    DESC
)
```

Ranks customers based on total purchases.

---

# 🎯 AI Dashboard Measures

## Best Territory

```DAX
Best Territory =
TOPN(
    1,
    VALUES('Sales Data'[Territory]),
    [Total Sales]
)
```

Identifies the highest-performing sales territory.

---

## Highest Profit Product

```DAX
Highest Profit Product =
TOPN(
    1,
    VALUES('Sales Data'[ProductName]),
    [Total Profit]
)
```

Returns the product contributing the highest profit.

---

# 📊 KPI Measures Used Across Dashboards

* Total Sales
* Total Profit
* Total Orders
* Total Customers
* Profit Margin %
* ROI
* Average Order Value
* Revenue per Customer
* Quantity Sold
* Average Selling Price
* Previous Year Sales
* YoY Growth %
* Running Total Sales
* Product Rank
* Customer Rank

---

# 💡 DAX Concepts Demonstrated

* Aggregation Functions
* Time Intelligence
* DIVIDE Function
* CALCULATE
* FILTER
* ALL
* DISTINCTCOUNT
* RANKX
* SAMEPERIODLASTYEAR
* Context Transition
* KPI Development

---

## 📌 Notes

* Measures were designed to support interactive dashboards using slicers and filters.
* Time Intelligence measures require a properly configured **Calendar Table** with an active relationship to the sales table.
* Ranking measures are used in Top N analyses and leaderboard visuals.
* KPI measures power Executive, Sales, Customer, Product, Geographic, Profit Analysis, and AI Insights dashboards.
