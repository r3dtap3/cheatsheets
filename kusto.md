# Kusto Query Language (KQL) Cheat Sheet with Examples

## Basic Query Structure
- **Select all columns**: `TableName`
  - **Example**: `MyTable`
- **Select specific columns**: `TableName | project Column1, Column2`
  - **Example**: `MyTable | project Name, Age`

## Filtering Data
- **Basic filter**: `| where Column == "value"`
  - **Example**: `MyTable | where Age == 30`
- **Multiple conditions**: `| where Column1 == "value1" and Column2 == "value2"`
  - **Example**: `MyTable | where Age == 30 and City == "New York"`
- **In list**: `| where Column in ("value1", "value2")`
  - **Example**: `MyTable | where IPAddress in ("10.10.6.129", "10.10.7.40")`

## Sorting Data
- **Ascending**: `| sort by Column asc`
  - **Example**: `MyTable | sort by Age asc`
- **Descending**: `| sort by Column desc`
  - **Example**: `MyTable | sort by Age desc`

## Aggregation
- **Count**: `| summarize count()`
  - **Example**: `MyTable | summarize count()`
- **Sum**: `| summarize sum(Column)`
  - **Example**: `MyTable | summarize sum(Salary)`
- **Average**: `| summarize avg(Column)`
  - **Example**: `MyTable | summarize avg(Age)`
- **Group By**: `| summarize count() by Column`
  - **Example**: `MyTable | summarize count() by City`

## Distinct Values
- **Unique rows**: `| distinct Column`
  - **Example**: `MyTable | distinct City`
- **Unique count**: `| summarize dcount(Column)`
  - **Example**: `MyTable | summarize dcount(City)`

## Joining Tables
- **Inner join**: `Table1 | join kind=inner Table2 on CommonColumn`
  - **Example**: `Orders | join kind=inner Customers on CustomerID`
- **Outer join**: `Table1 | join kind=outer Table2 on CommonColumn`
  - **Example**: `Orders | join kind=outer Customers on CustomerID`

## Time Operations
- **Time range**: `| where Timestamp between (datetime(2021-01-01) .. datetime(2021-12-31))`
  - **Example**: `MyTable | where Timestamp between (datetime(2021-01-01) .. datetime(2021-12-31))`
- **Time format**: `| extend FormattedTime = format_datetime(Timestamp, 'yyyy-MM-dd')`
  - **Example**: `MyTable | extend FormattedTime = format_datetime(Timestamp, 'yyyy-MM-dd')`

## String Operations
- **Concatenation**: `| extend NewColumn = strcat(Column1, Column2)`
  - **Example**: `MyTable | extend FullName = strcat(FirstName, LastName)`
- **Substring**: `| extend Sub = substring(Column, 0, 5)`
  - **Example**: `MyTable | extend Initials = substring(Name, 0, 2)`

## Control Commands
- **Show tables**: `.show tables`
  - **Example**: `.show tables`
- **Show schema**: `.show table TableName schema`
  - **Example**: `.show table MyTable schema`

## Miscellaneous
- **Limit rows**: `| take 10`
  - **Example**: `MyTable | take 10`
- **Skip rows**: `| skip 10`
  - **Example**: `MyTable | skip 10`
- **Rename column**: `| project-rename NewColumnName=OldColumnName`
  - **Example**: `MyTable | project-rename NewAge=Age`
