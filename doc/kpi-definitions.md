# KPI Definitions

## Sales MTD

**Business definition**  
Sales from the start of the current month through the date context selected in `Date[Date]`.

**Calculation**  
`CALCULATE(SUM('Sales'[Sales Amount]), DATESMTD('Date'[Date]))`

**Existing model fields**  
- `Sales[Sales Amount]`
- `Date[Date]`
- `Sales[OrderDateKey]`
- `Date[DateKey]`

**Format**  
Currency: `$#,0.00`

## Sales YTD

**Business definition**  
Sales from the start of the fiscal or calendar year represented by the current `Date[Date]` context through the selected date.

**Calculation**  
`CALCULATE(SUM('Sales'[Sales Amount]), DATESYTD('Date'[Date]))`

The measure depends on the active relationship from `Sales[OrderDateKey]` to `Date[DateKey]`.

**Existing model fields**  
- `Sales[Sales Amount]`
- `Date[Date]`
- `Sales[OrderDateKey]`
- `Date[DateKey]`

**Format**  
Currency: `$#,0.00`

## Sales Month-over-Month Change

**Business definition**  
Percentage change between current-month-to-date sales and sales for the equivalent previous-month date range.

**Calculation**  
- Current month: `CALCULATE(SUM('Sales'[Sales Amount]), DATESMTD('Date'[Date]))`
- Previous month: `CALCULATE(SUM('Sales'[Sales Amount]), DATEADD('Date'[Date], -1, MONTH))`
- Change: `(Current Month Sales - Previous Month Sales) / Previous Month Sales`

The denominator is protected with `DIVIDE`, which avoids divide-by-zero errors and returns a blank where appropriate.

**Existing model fields**  
- `Sales[Sales Amount]`
- `Date[Date]`
- `Sales[OrderDateKey]`
- `Date[DateKey]`

**Format**  
`0.0%;-0.0%;0.0%`

## Report Measures

### Year-to-Date Sales card

Uses `Sales YTD`.

**Business purpose**  
Shows the accumulated sales amount in the selected date context.

### Year-to-Date Sales by Product Category chart

Uses:

- Category: `Product[Category]`
- Value: `Sales YTD`

**Business purpose**  
Compares year-to-date sales across product categories.