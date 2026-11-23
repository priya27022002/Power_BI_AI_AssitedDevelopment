# Data Dictionary

## Tables, Columns, and Measures Used by the Report Visuals

### Card: Year-to-Date Sales

| Table name | Column / measure name | Data type | Business description |
|---|---|---|---|
| `Sales` | `Sales YTD` | DAX measure; format `$#,0.00` | Calculates sales for the year-to-date date context using `DATESYTD('Date'[Date])`. |
| `Sales` | `Sales Amount` | `double` | Sales amount value stored in the `Sales` table. |
| `Sales` | `OrderDateKey` | `int64` | Date key used to connect sales records to `Date[DateKey]`. |
| `Date` | `Date` | `dateTime` with underlying date data type | Date value used for the year-to-date date context. |
| `Date` | `DateKey` | `int64` | Integer date key used by the active relationship from `Sales[OrderDateKey]`. |

### Column Chart: Year-to-Date Sales by Product Category

| Table name | Column / measure name | Data type | Business description |
|---|---|---|---|
| `Product` | `Category` | `string` | Product category used to group year-to-date sales. |
| `Sales` | `Sales YTD` | DAX measure; format `$#,0.00` | Year-to-date sales plotted as the Y-axis value for each product category. |

## Relationship Dependency

`Sales YTD` is evaluated in the active Date context created by:

- `Sales[OrderDateKey]` to `Date[DateKey]`
- Cardinality: many-to-one
- Filter direction: single-direction from `Date` to `Sales`

The chart additionally depends on:

- `Product[Category]`
- `Sales[ProductKey]` to `Product[ProductKey]`