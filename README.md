## 📂 Dataset Description

Five CSV datasets were provided and loaded into Power BI via Power Query. All datasets are available in the `/datasets` folder of this repository.

| File | Rows | Description |
|---|---|---|
| `sales_transactions.csv` | 5,000 | Core fact table containing all sales transactions including quantity, price, discount, and return status |
| `customers.csv` | 1,200 | Customer profiles including age, gender, city, loyalty card status and customer segment |
| `products.csv` | 60 | Product catalogue containing category, sub-category, cost price, unit price and reorder level |
| `branches.csv` | 6 | Branch information including location, manager name, opening date and store size |
| `date.csv` | 731 | Date dimension table covering the full 2023 to 2024 trading period |

### Data Quality Actions Taken

| Issue | Action Taken |
|---|---|
| 107 blank Customer IDs in sales_transactions | Replaced with "Unknown" to preserve transaction integrity |
| No duplicate rows found in any table | Removed Duplicates step applied to all 5 tables as best practice |
| All column names contained underscores | Renamed to professional readable format across all tables |
| Data types not set | Correct data types assigned to every column in all 5 tables |

---
