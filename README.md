# Sales-Insights-Data-Analysis (creating  interactive dashboard using Power BI)
The objective of the report is to analyze and present comprehensive insights into sales, profit, orders, profit margin, and various comparisons. It aims to provide a clear understanding of key performance indicators and trends using Power BI.

## Sales Dashboard Features

Calculate Total Sales
Quickly view the total sales for your selected time period to understand how much revenue you’ve brought in.

Check Total Profit
Find out how much profit you’ve made, giving you a clear picture of your financial performance.

Track Order Volume
See how many orders were placed in a given period to uncover patterns and trends in customer buying behavior.

View Profit Margins
Get a percentage-based view of your profit margins to evaluate how efficiently you're generating profit from sales.

Compare Product Sales with Previous Year
See how each product is performing compared to the same period Previous year—spotting which items are gaining or losing traction.

Compare Monthly Sales with previous Year
Look at month-over-month sales changes from the current and previous year to identify seasonal trends or shifts.

Top 5 Cities by Sales
Instantly identify your best-performing cities with a visual showing the top 5 based on total sales.

Compare Profit by Sales Channel with previous Year
See how profits from different sales channels have changed year-over-year, highlighting what's working and what's not.

Customer Sales Comparison
Break down sales by customer and compare their activity to last year to identify loyal or high-value customers.

Interactive Filters
Use slicers to filter data by date, city, product, and sales channel—making it easy to explore exactly what you need.


## Steps to follow for an end-to-end Power BI Project

1) Gather Data
2) Power Querry – Data Extract, Transform & Load
3) Create a Date Table
   ->Code for Creating Date Table in Power BI
     DAX DateTable = 
ADDCOLUMNS (
    //CALENDAR(DATE(2020,1,1), DATE(2024,12,31)),
    CALENDARAUTO(),
    "Year", YEAR([Date]),
    "Quarter", "Q" & FORMAT(CEILING(MONTH([Date])/3, 1), "#"),
    "Quarter No", CEILING(MONTH([Date])/3, 1),
    "Month No", MONTH([Date]),
    "Month Name", FORMAT([Date], "MMMM"),
    "Month Short Name", FORMAT([Date], "MMM"),
    "Month Short Name Plus Year", FORMAT([Date], "MMM,yy"),
    "DateSort", FORMAT([Date], "yyyyMMdd"),
    "Day Name", FORMAT([Date], "dddd"),
    "Details", FORMAT([Date], "dd-MMM-yyyy"),
    "Day Number", DAY ( [Date] )
)

4) Create Data Model in Power BI Desktop
Design and create a data model that represents the relationships between different tables in your data. Establish proper relationships, define keys, and establish hierarchies if needed. This step is crucial for accurate analysis and visualization

5) Develop Reports in Power BI Desktop
->Use the Power BI Desktop application to create reports based on your data model. Add visualizations such as charts, tables, and maps to represent the data effectively. Apply filters, slicers, and drill-through functionalities to allow users to interact with the data.
Create Report Background in PowerPoint
Create Slicers – Date, City, Product, and Channel
Create Dax measures
Create Visuals:
-> Sales By Product and Comparing it with last year’s Sales.
-> Sales By Month and Comparing it with last year’s Sales.
-> Sales of top 5 Cities
-> Compare Profit by channel with Previous year’s Profit
-> Sales By Customer and Comparing it with last year’s Sales
-> Create Cards for Sales, Profit, Profit Margin & Product Sold

6) Implementing DAX Calculations
   //Measures Total Sales
Sales = SUM(Sales_Data[Sales])

//Measures Previous Year Toal Sales
Sales PY = CALCULATE([Sales], SAMEPERIODLASTYEAR(DateTable[Date]))

//Diffrence Between Current Year Sales & Previous Year Sales
Sales vs PY = [Sales] - [Sales PY]

//Percentage Increase or Decrease in sales year on year (YOY%)
Sales vs py % = DIVIDE([Sales vs PY],[Sales],0)



>> Products Sold = SUM(Sales_Data[Order Quantity])
>> Profit = SUM(Sales_Data[Profit]) 
>> Profit LY = CALCULATE([Profit], SAMEPERIODLASTYEAR(DateTable[Date]))
>> Profit Vs LY = [Profit]- [Profit LY]
>> Profit vs LY % = [Profit Vs LY]/[Profit]
>> Profit Margin = DIVIDE([Profit],[Sales],0)
>> Total Cost = SUM(Sales_Data[Total Cost])


## Dataset Used
<a href="https://github.com/vikash9621/Sales-Insights-Data-Analysis-in-Power-BI/blob/main/Sales%20Data%20Analysis.xlsx">sales dataset</a>

## Dashboard Interaction
<a href="https://github.com/vikash9621/Sales-Insights-Data-Analysis-in-Power-BI/blob/main/Screenshot%202025-04-28%20204755.png">dashboard</a>

## Dashboard
![Screenshot 2025-04-28 204755](https://github.com/user-attachments/assets/51a77346-579f-4f8a-8a72-74a8b36ad609)

   
