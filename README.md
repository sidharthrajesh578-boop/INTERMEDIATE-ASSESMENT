This assignment is a Power BI Module End Evaluation (15 marks) built around a sales dataset, SalesData_1000Rows_WithIssues_copy.csv. The dataset has 1,020 rows and 11 columns: OrderID, OrderDate, CustomerName, Region, Product, Category, Quantity, UnitPrice, Sales, Cost and Profit. It was deliberately seeded with problems: missing values, 18 duplicate rows, and dates stored as text in dd-mm-yyyy format. The task is to take this raw data through the full Power BI workflow: cleaning, visualization and DAX analysis.

Q1: Data Cleaning and Loading

The raw CSV was imported into Power BI and prepared in Power Query Editor. The cleaning steps were:

Duplicates removed: the 18 duplicate rows were deleted, leaving about 1,002 rows.
Missing values handled: blank text fields (CustomerName, Region, Product) were replaced with “Unknown”, and rows with missing OrderDate or financial values (UnitPrice, Sales, Cost, Profit) were removed.
Dates standardized: OrderDate was converted from text to a true Date type using the UK/India locale, so that 22-06-1991 is read as 22 June 1991.
Loaded: the cleaned table was loaded into the model as SalesData.
Q2: Visualizations and Insights 

Three visuals were built on the cleaned data:

Pie chart: the number of orders (Count of OrderID) by region. East has the most orders (260), followed by South (252), West (230) and North (227).
Column chart: the top 5 products by number of orders, using a Top N filter. The results are Monitor, Laptop, Bookshelf, Cabinet and Headphones.
Line chart: profit trend over time, by year, from about 1970 to 2025. The last point drops because the final year contains only partial data.
Q3: DAX Calculations 

Three DAX objects were created:

Calculated table EastRegionOrders: FILTER(SalesData, SalesData[Region] = "East") returns only the East region’s orders.
Calculated column ProfitCostDifference: SalesData[Profit] - SalesData[Cost] computes the difference for every row.
Measure TotalProfit: SUM(SalesData[Profit]) gives total profit, shown on a card as ₹5.117016M.
