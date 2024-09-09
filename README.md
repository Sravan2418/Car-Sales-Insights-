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

## Quantified Results:

Achieved a 23.59% increase in YTD sales compared to the previous year, reaching $371.2M.
Identified that SUVs and black-colored cars were the most popular, driving the highest sales volumes.
Pinpointed regions with the highest sales growth, aiding in targeted marketing and inventory management.

## Conclusion: 
The Power BI dashboard effectively transformed raw sales data into actionable insights, enabling better decision-making across the sales, marketing, and inventory management teams. The interactive visualizations provided clear and concise information that helped the business track performance, understand market dynamics, and optimize strategies.

