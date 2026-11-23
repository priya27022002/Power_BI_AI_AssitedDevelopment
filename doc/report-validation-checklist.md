# Report Accuracy and Completeness Checklist

## Measure validation

- [ ] Confirm `Sales YTD` equals the sum of `Sales[Sales Amount]` for the selected year and date context.
- [ ] Reconcile `Sales YTD` to the source workbook for at least one complete fiscal or calendar year.
- [ ] Confirm `Sales MTD` starts on the first day of the selected month and stops at the selected date.
- [ ] Confirm month-over-month comparison uses the intended previous-month date range.
- [ ] Confirm blank, zero, and missing prior-period values behave as intended.
- [ ] Verify that `Sales MTD`, `Sales YTD`, and `Sales Month-over-Month Change` remain correct when a category filter is applied.
- [ ] Verify the `Sales Amount` format is a currency format in report visuals.

## Date validation

- [ ] Confirm `Date[DateKey]` and `Sales[OrderDateKey]` contain matching integer values.
- [ ] Confirm `Date[Date]` contains a continuous date range without gaps.
- [ ] Confirm the active relationship is `Sales[OrderDateKey]` to `Date[DateKey]`.
- [ ] Confirm fiscal-year behavior is valid if `Fiscal Year` should determine YTD boundaries.
- [ ] Confirm Due Date and Ship Date reporting does not accidentally use Order Date unless explicitly intended.

## Relationship validation

- [ ] Confirm each dimension key is unique on the one-side table.
- [ ] Confirm no duplicate or null keys exist on the relationship one-side.
- [ ] Confirm fact-table foreign keys have matching dimension keys where applicable.
- [ ] Confirm all existing relationships use single-direction filtering unless a verified many-to-many requirement exists.
- [ ] Confirm `Sales[SalesOrderLineKey]` is unique on `SalesOrder` before relying on the relationship.
- [ ] Confirm `Sales[ResellerKey]` remains excluded from reporting until a matching table and relationship exist.

## Report visual validation

- [ ] Confirm the card title is “Year-to-Date Sales”.
- [ ] Confirm the card uses `Sales YTD` only.
- [ ] Confirm the column chart title is “Year-to-Date Sales by Product Category”.
- [ ] Confirm the X-axis uses `Product[Category]` and the Y-axis uses `Sales YTD`.
- [ ] Confirm product-category totals sum to the overall YTD card total.
- [ ] Confirm category names are complete and no category is duplicated by spelling or whitespace differences.
- [ ] Confirm the card and chart respond consistently to existing report filters.

## Data quality and refresh

- [ ] Profile null or blank values in key and numeric columns.
- [ ] Verify numeric conversion values and date conversion values in source refresh logs.
- [ ] Confirm no duplicate rows were removed from valid transactions.
- [ ] Confirm the workbook location is accessible for refresh.
- [ ] Confirm credentials or gateway configuration are valid for scheduled refresh.
- [ ] Compare source row count and sales total before and after refresh.

## Completeness

- [ ] Document all active, inactive, and missing relationships.
- [ ] Reconcile the report to source totals.
- [ ] Verify that the report opens and refreshes without errors.
- [ ] Export or screenshot the final report for sign-off after Desktop verification.
