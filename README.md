# Sales Dashboard

## Table of Contents

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#Tools)
- [Data Analysis processes](#Data-Analysis)
- [Findings](#resultsfindings)
- [Recommendations](#recommendations)
  

## Project Overview

This data analysis project aims to provide insights into the sales performance of an imaginary store over the past 3 years.
This project focuses on analyzing comprehensive sales data and creating insightful visualizations using Power BI. The goal is to derive actionable insights into key financial metrics, such as revenue, costs, profit margins, cumulative sales, etc. Additionally, the project evaluates salespersons' performance, highlighting top performers based on sales and profit metrics. 

By analyzing various aspects of the sales data, I seek to identify trends, make data-driven recommendations, and gain a deeper understanding of the company's performance.


## Data Sources

Sales Data: The primary dataset used for this analysis is the "sales_data.xlxs" file, containing detailed information about Products, Customers, Locations, Sales Person, and sales data (including 2020, 2021, and 2022 ) in 3 separate sheets, and each sale made by the company.

## Tools

- Excel - Data Source
- Power Query - Data Cleaning and Preparation
- Power BI - Creating reports
- DAX - Calculate Different Metrics

## Data Analysis

### Data Cleaning/Preparation

In the initial data preparation phase, I performed the following tasks:
1. Data loading and inspection.
2. Handling missing values.
3. Data cleaning and formatting.
4. Append sales data from 3 different tables.
5. Creating data Model.

### Data Model
![Data Model](https://github.com/tasnimxpress/SalesDashboard/blob/main/Data%20Model.png)

### Exploratory Data Analysis

EDA involved exploring the sales data to answer key questions, such as:

- What is the overall revenue generated?
- What are the total costs incurred?
- What is the total profit and profit margin?
- How do revenue and profit margins trend over time?
- What are the cumulative sales over the years?
- Which product categories contribute the most to profits?
- How do revenue, total costs, and profit compare by year?
- Who are the top-performing salespersons by total sales and profit?
- Sales, profit, and profit percentages for each salesperson.

### Calculations to find insights

Some DAX/Calculation I worked with:

```Cumulative Sales
Cumulative Sales = IF(
                    NOT ISBLANK(MeasureTbl[Revenue]),
                    CALCULATE([Revenue],
                    FILTER(ALLSELECTED(Dates[Date]),Dates[Date]<=MAX(Dates[Date]))),
                    BLANK()
                    )
```

```Revenue/Total Sales
Revenue = SUMX(Sales,Sales[Quantity]*Sales[Price])
```

```Total Cost
TotalCost = SUMX(Sales,Sales[Quantity]*RELATED('Product'[Cost]))
```

```Revenue for Last year 
RevenuePY = IF(
            NOT ISBLANK(MeasureTbl[Revenue]),
            CALCULATE(MeasureTbl[Revenue],DATEADD(Dates[Date],-1,YEAR)),
            BLANK()
            )
```

```Profit Margin
ProfitMargin = DIVIDE(MeasureTbl[Profit],MeasureTbl[Revenue])
```

```Profit Percentage
Profit_Percentage = DIVIDE([Profit],[TotalCost])
```

```Profit Target Indicator
Profit Target Indicator = IF([Profit_Percentage]>[Profit Target],2,1)
```

### Dashboard Creation
Power BI was used to create interactive dashboards, providing a visual representation of the analyzed data.

- **Sales Analysis Dashboard:** Includes overall sales metrics, revenue and profit margin trends, cumulative sales, and profits by product category.
![Sales Dashboard](https://github.com/tasnimxpress/SalesDashboard/blob/main/Dashboard/Sales%20analysis%20dashboard%20.png)

- **Salespersons Performance Dashboard:** Highlights individual salesperson performance in terms of sales, profit, and profit percentage.
![Salespersons Performance](https://github.com/tasnimxpress/SalesDashboard/blob/main/Dashboard/Sales%20Persons%20Performance.png)
![Total Sales Line Chart](https://github.com/tasnimxpress/SalesDashboard/blob/main/Dashboard/Total%20Sales%20%26%20Profit%20Chart.png)


## Results/Findings

The analysis results are summarized as follows:

1. Total Costs are 17.32 Million, Total revenue 25.66 Million, Whereas, Total Profit is 8.34 Million with a 32.52% profit margin.
2. The company's sales have been steadily increasing over the past year, with a noticeable peak during January and February.
3. Product Category Kids & Toys is the best-performing category in terms of profits, with the highest profitability at 43.18%.
4. Revenue and Profit Margin: Displayed quarterly, showing trends and fluctuations over time.
5. Cumulative Sales over Period: A line chart illustrating the growth of cumulative sales from 2020 to 2022.
6. Revenue, Total Costs & Profit by Year: A bar chart comparing annual revenue, total costs, and profit, indicating financial performance across the years.
   
**Salespersons Performance Dashboard**

1. Top Salespersons by Total Sales: Kenneth Bradley led with $0.68M in sales, followed by Ryan Welch and Bobby Russell.
2. Profit Performance vs. Sales Performance: Jeremy Mendoza achieved the highest profit percentage at 52.24%, with Jerry Perry and Scott Mason also showing consistent profit performance. While Kenneth Bradley had the highest total sales, he did not have the highest profit percentage.
3. Target Profit Achievement: The data reveals that only a few salespersons met the target profit percentage. Most salespeople did not achieve the target. Notably, Kenneth Bradley is the only top salesperson by sales who also met the target profit percentage.

## Recommendations

Based on the analysis, we recommend the following actions:
- Need further investigate to find out why top salespeople failed to achieve profit target. Compare salespersons' performance against industry benchmarks to identify areas for improvement and set realistic targets.
- Focus on expanding and promoting products in the category Kids & Toys, Marketing in the stationary category can be expanded.
- While plastics are the least performing category, this department can investigate further.
- Implement a customer segmentation strategy to target high customers effectively.

## Limitations

The analysis is based on historical data, which may not fully capture future market dynamics or unforeseen events that could impact sales performance. Factors affecting profit margins, such as changes in cost structures or pricing strategies, are not explicitly addressed in the analysis.

💻
