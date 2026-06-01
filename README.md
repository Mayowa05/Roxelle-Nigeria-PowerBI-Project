## 🗂️ Data Model

A Star Schema was built with `sales_transactions` as the central fact table and four surrounding dimension tables. All relationships were configured manually to ensure accuracy.

### Relationship Configuration

| Dimension Table | Key Column | Fact Table | Key Column | Cardinality | Filter Direction |
|---|---|---|---|---|---|
| customers | Customer ID | sales_transactions | Customer ID | One to Many | Single |
| products | Product ID | sales_transactions | Product ID | One to Many | Single |
| branches | Branch ID | sales_transactions | Branch ID | One to Many | Single |
| date | Date | sales_transactions | Transaction Date | One to Many | Single |

### Design Decisions

- **Single filter direction** was applied to all relationships to prevent ambiguous filter paths and ensure correct aggregations across all visuals
- **Assume Referential Integrity** was left unticked on all relationships because 107 transactions contained "Unknown" Customer IDs that do not exist in the customers table
- **No Many-to-Many relationships** exist in this model
- A dedicated **Measures table** was created to store all DAX measures separately from the data tables

### Star Schema Screenshot

![Data Model](images/star_schema.png)

---
