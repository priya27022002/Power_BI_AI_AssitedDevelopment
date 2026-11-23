# Data Dictionary

## Tables, Columns, and Measures Used by the Report Visuals

### Card: Year-to-Date Sales

| Table name | Column / measure name | Data type | Business description |
|---|---|---|---|
| `Sales` | `Sales YTD` | DAX measure; format `$#,0.00` | Calculates year-to-date sales by filtering `Sales[OrderDateKey]` through date keys returned by `Date[Date]` and `Date[DateKey]`. |
| `Sales` | `Sales Amount` | `double` | Sales amount value stored in the `Sales` table. |
| `Sales` | `OrderDateKey` | `int64` | Date key used to relate sales records to dates in the `Date` table. |
| `Date` | `Date` | `dateTime` with underlying date data type | Date value used for the year-to-date date context. |
| `Date` | `DateKey` | `int64` | Integer date key corresponding to dates used by the `Sales YTD` measure. |

### Column Chart: Year-to-Date Sales by Product Category

| Table name | Column / measure name | Data type | Business description |
|---|---|---|---|
| `Product` | `Category` | `string` | Product category used to break down year-to-date sales. |
| `Sales` | `Sales YTD` | DAX measure; format `$#,0.00` | Sales total accumulated year to date, plotted as the Y-axis value for each product category. |

## Measure Dependencies

`Sales YTD` uses the following existing model objects:

- `Sales[Sales Amount]`
- `Sales[OrderDateKey]`
- `Date[Date]`
- `Date[DateKey]`

The measure uses `Date[Date]` to establish the DATESYTD date context and `Date[DateKey]` with `TREATAS` to filter `Sales[OrderDateKey]`.