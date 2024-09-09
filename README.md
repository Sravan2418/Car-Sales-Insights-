# Car Sales Data Analytics Using Power BI 

## Problem Statement: 
The goal of this project was to develop a comprehensive Power BI dashboard to analyze car sales data stored in Azure Data Lake Storage Gen2. The objective was to provide real-time insights into key performance indicators (KPIs) to support data-driven decision-making. The dashboard aimed to address several business needs, such as tracking sales trends, understanding average price changes, and visualizing the geographical distribution of sales.

## Data Handling and Transformation:

-> Data Ingestion: The car sales data was stored in Azure Data Lake Storage Gen2. The data was connected to Power BI using an account sign-in key.
-> Data Cleaning: Data cleaning was performed using Power Query to ensure quality. This involved checking for errors, removing null values, and validating data types, ensuring the dataset was 100% accurate for analysis.
-> Calendar Table Creation: A calendar table was created using DAX commands to enable time-based calculations such as Year-to-Date (YTD), Month-to-Date (MTD), and Year-over-Year (YOY) metrics. The table was essential for the time intelligence functions in Power BI.

## Data Modeling and Relationships:

A data model was built by linking the date column in the car sales data to the date column in the calendar table, establishing a many-to-one relationship. This connection was crucial for accurate time-based aggregations and visualizations.

## Solution and Dashboard Development:

### Sales KPIs Visualization:

YTD Total Sales: Displayed the total sales amount for the current year-to-date using card visuals. This metric helped track sales performance compared to previous periods.
MTD Total Sales: Showed the total sales amount for the current month-to-date, enabling more granular tracking of sales trends.
YOY Growth in Total Sales: Calculated the growth rate in sales compared to the previous year, highlighting areas of improvement or decline.
Difference Between YTD and Previous YTD Sales: Showcased the absolute and percentage difference between current and previous year's sales.
Average Price Analysis:

YTD Average Price: Calculated and visualized the average car price year-to-date, providing insights into pricing trends.
MTD Average Price: Displayed the average car price for the current month, helping identify short-term pricing changes.
YOY Growth in Average Price: Demonstrated the annual growth or decline in car prices, offering a clear view of market pricing dynamics.
Cars Sold Metrics:

YTD Cars Sold: Visualized the total number of cars sold year-to-date, offering a snapshot of sales volume performance.
MTD Cars Sold: Showed the number of cars sold month-to-date, helping identify trends within the current month.
YOY Growth in Cars Sold: Highlighted the annual change in the number of cars sold, providing a comparative view against the previous year.

## Dashboard Insights and Interpretation:

1. Sales Weekly Trend: A line chart displayed the weekly trend of YTD sales, identifying peak sales weeks and seasonal patterns. The highest sales week was marked for easy identification.
2. Sales by Body Style and Color: Pie charts illustrated the distribution of YTD total sales by car body style and color, revealing consumer preferences.
3. Geographical Distribution: A map chart showcased YTD sales data by dealer region, helping identify top-performing areas and potential market expansion opportunities.
4. Company-Wise Sales Trend: A grid displayed sales trends for each car company, comparing YTD sales figures and providing insights into brand performance.

## DAX Commands Used : 

### 1. Calendar Table :

Date Table = CALENDAR(MIN(carsalesdata[Date]), MAX(carsalesdata[Date]))

Year = YEAR('Date Table'[Date])

Month = FORMAT('Date Table'[Date], "MMMM")

Week = WEEKNUM('Date Table'[Date])

### 2. Key Performance Indicators (KPIs) :

YTD Total_Sales = TOTALYTD(SUM(carsalesdata[Price ($)]), 'Date Table'[Date])

PYTD Total_Sales = CALCULATE(SUM(carsalesdata[Price ($)]), SAMEPERIODLASTYEAR('Date Table'[Date]))

Sales Difference = [YTD Total_Sales] - [PYTD Total_Sales]

Sales Diff Colour = IF([Sales Difference] > 0, "Green", "Red")

YOY Sales Growth = [Sales Difference] / [PYTD Total_Sales]

MTD Total_Sales = TOTALMTD(SUM(carsalesdata[Price ($)]), 'Date Table'[Date])

MTD KPI = CONCATENATE("MTD Total Sales: ", FORMAT([MTD Total_Sales]/1000000, "$0.00M"))

### 3. Average Price Analysis :

Avg Price = SUM(carsalesdata[Price ($)]) / COUNT(carsalesdata[Car_id])

YTD AVG Price = TOTALYTD([Avg Price], 'Date Table'[Date])

PYTD AVG Price = CALCULATE([Avg Price], SAMEPERIODLASTYEAR('Date Table'[Date]))

AVG Price Difference = [YTD AVG Price] - [PYTD AVG Price]

AVG Price Colour = IF([AVG Price Difference] > 0, "Green", "Red")

YOY AVG Price Growth = [AVG Price Difference] / [PYTD AVG Price]

MTD AVG Price = TOTALMTD([Avg Price], 'Date Table'[Date])

MTD AVG Price KPI = CONCATENATE("MTD AVG Price: ", FORMAT([MTD AVG Price]/1000, "$0.00K"))

### 4. Car Sold Metrics :

YTD Cars Sold = TOTALYTD(COUNT(carsalesdata[Car_id]), 'Date Table'[Date])

PYTD Cars Sold = CALCULATE(COUNT(carsalesdata[Car_id]), SAMEPERIODLASTYEAR('Date Table'[Date]))

Cars Sold Difference = [YTD Cars Sold] - [PYTD Cars Sold]

Cars Sold Colour = IF([Cars Sold Difference] > 0, "Green", "Red")

YOY Cars Sold Growth = [Cars Sold Difference] / [PYTD Cars Sold]

MTD Cars Sold = TOTALMTD(COUNT(carsalesdata[Car_id]), 'Date Table'[Date])

MTD Cars Sold KPI = CONCATENATE("MTD Cars Sold: ", FORMAT([MTD Cars Sold]/1000, "0.00"))

### 5. Additional Calculations for Visualizations :

Total Sales = SUM(carsalesdata[Price ($)])

Max Point = IF(MAXX(ALLSELECTED('Date Table'[Week]), [Total Sales]) = [Total Sales], MAXX(ALLSELECTED('Date Table'[Week]), [Total Sales]), BLANK())


## Quantified Results:

Achieved a 23.59% increase in YTD sales compared to the previous year, reaching $371.2M.
Identified that SUVs and black-colored cars were the most popular, driving the highest sales volumes.
Pinpointed regions with the highest sales growth, aiding in targeted marketing and inventory management.

## Conclusion: 
The Power BI dashboard effectively transformed raw sales data into actionable insights, enabling better decision-making across the sales, marketing, and inventory management teams. The interactive visualizations provided clear and concise information that helped the business track performance, understand market dynamics, and optimize strategies.

## Dashboards : 

<img width="1362" alt="page 1 " src="https://github.com/user-attachments/assets/fdb44fba-4dad-46d8-a31d-7b2e8f5d49cd">

<img width="1363" alt="page 2 " src="https://github.com/user-attachments/assets/148f451b-f56e-4443-8f0a-d6170cb37705">

## Link : https://app.powerbi.com/reportEmbed?reportId=e5e61871-92c0-43bd-9aa7-7095d11b2a89&autoAuth=true&ctid=4278a402-1a9e-4eb9-8414-ffb55a5fcf1e
