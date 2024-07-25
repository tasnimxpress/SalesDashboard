# SalesDashboard

## Table of Contents

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Recommendations](#recommendations)

### Project Overview
---

This data analysis project aims to provide insights into the sales performance of an imaginary store over the past 3 years.
This project focuses on analyzing comprehensive sales data and creating insightful visualizations using Power BI. The goal is to derive actionable insights into key financial metrics, such as revenue, costs, profit margins, and cumulative sales etc. Additionally, the project evaluate the performance of salespersons, highlighting top performers based on sales and profit metrics. 
By analyzing various aspects of the sales data, I seek to identify trends, make data-driven recommendations, and gain a deeper understanding of the company's performance.


### Data Sources

Sales Data: The primary dataset used for this analysis is the "sales_data.xlxs" file, containing detailed information about Products, Customers, Locations, Sales Person, and sales data (including 2020, 2021, and 2022 ) in 3 separate sheets, and each sale made by the company.

### Tools

- Excel - Data Source
- Power Query - Data Cleaning and Preparation
- Power BI - Creating reports
- DAX - Calculate Different Metrics


### Data Cleaning/Preparation

In the initial data preparation phase, we performed the following tasks:
1. Data loading and inspection.
2. Handling missing values.
3. Data cleaning and formatting.
4. Append sales data from 3 different tables.


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


### Data Analysis

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

### Results/Findings

The analysis results are summarized as follows:
1. The company's sales have been steadily increasing over the past year, with a noticeable peak during the holiday season.
2. Product Category A is the best-performing category in terms of sales and revenue.
3. Customer segments with high lifetime value (LTV) should be targeted for marketing efforts.

### Recommendations

Based on the analysis, we recommend the following actions:
- Invest in marketing and promotions during peak sales seasons to maximize revenue.
- Focus on expanding and promoting products in Category A.
- Implement a customer segmentation strategy to target high-LTV customers effectively.

### Limitations

I had to remove all zero values from budget and revenue columns because they would have affected the accuracy of my conclusions from the analysis. There are still a few outliers even after the omissions but even then we can still see that there is a positive correlation between both budget and number of votes with revenue.

### References

1. SQL for Businesses by werty.
2. [Stack Overflow](https://stack.com)

😄

💻

|Heading1|Heading2|
|--------|--------|
|Content|Content2|
|Python|SQL|

`column_1`

**bold**

*italic*
