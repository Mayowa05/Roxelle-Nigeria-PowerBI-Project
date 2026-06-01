## 📊 DAX Measures Documentation

All measures are stored in a dedicated **Measures** table. Below is the full documentation of every measure created.

| Measure Name | DAX Formula | Purpose |
|---|---|---|
| Total Revenue | `SUM(sales_transactions[Revenue After Discount])` | Sum of all revenue after discounts applied |
| Total Cost | `SUMX(sales_transactions, sales_transactions[Quantity] * RELATED(products[Cost Price]))` | Total cost calculated row by row using product cost price |
| Total Profit | `[Total Revenue] - [Total Cost]` | Net profit across all transactions |
| Profit Margin % | `DIVIDE([Total Profit], [Total Revenue], 0)` | Overall profit margin as a percentage |
| Total Transactions | `DISTINCTCOUNT(sales_transactions[Transaction ID])` | Count of unique transactions |
| Return Rate % | `DIVIDE(COUNTROWS(FILTER(sales_transactions, sales_transactions[Is Returned] = 1)), [Total Transactions], 0)` | Percentage of transactions that resulted in a return |
| Avg Basket Size | `DIVIDE([Total Revenue], [Total Transactions], 0)` | Average revenue per transaction |
| MoM Revenue % | `DIVIDE([Total Revenue] - CALCULATE([Total Revenue], DATEADD('date'[Date], -1, MONTH)), CALCULATE([Total Revenue], DATEADD('date'[Date], -1, MONTH)), 0)` | Month over month revenue change as a percentage |
| YoY Revenue % | `DIVIDE([Total Revenue] - CALCULATE([Total Revenue], SAMEPERIODLASTYEAR('date'[Date])), CALCULATE([Total Revenue], SAMEPERIODLASTYEAR('date'[Date])), 0)` | Year over year revenue growth as a percentage |
| Revenue Lost to Discount | `SUMX(sales_transactions, sales_transactions[Quantity] * sales_transactions[Unit Price] * (sales_transactions[Discount %] / 100))` | Total revenue sacrificed through discounting |

### Calculated Columns

| Column | Table | Formula | Purpose |
|---|---|---|---|
| Revenue After Discount | sales_transactions | Created in Power Query | Quantity x Unit Price x (1 - Discount% / 100) |
| Profit Per Transaction | sales_transactions | `(sales_transactions[Unit Price] * sales_transactions[Quantity]) - (RELATED(products[Cost Price]) * sales_transactions[Quantity])` | Profit generated per individual transaction |
| Age Group | customers | `IF(customers[Age] >= 56, "56+", IF(customers[Age] >= 46, "46-55", IF(customers[Age] >= 36, "36-45", IF(customers[Age] >= 26, "26-35", "18-25"))))` | Buckets customer ages into 5 groups for analysis |

---
