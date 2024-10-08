# Coffee Shop Sales Dashboard
## Problem Statement:
A local coffee shop chain seeks to understand its sales trends better to enhance business performance. The chain is interested in tracking key performance metrics like sales, orders, and product categories to spot opportunities for improvement and growth, particularly over the month of May 2023.

The goal of this analysis is to provide insights into product category sales, sales by store, and daily sales patterns.

## 1. ASK

**Key Questions for Analysis:**

### 1. Total Sales Analysis:
- Calculate the total sales for each month.
- Determine the month-on-month increase or decrease in sales.
- Calculate the difference in sales between the selected month and the previous month.

### 2. Total Orders Analysis:
- Calculate the total number of orders for each respective month.
- Determine the month-on-month increase or decrease in the number of orders.
- Calculate the difference in the number of orders between the selected month and the previous month.

### 3. Total Quantity Sold Analysis:
- Calculate the total quantity sold for each respective month.
- Determine the month-on-month increase or decrease in the total quantity sold.
- Calculate the difference in the total quantity sold between the selected month and the previous month.

### 4. Calendar Heat Map:
- Implement a calendar heat map that dynamically adjusts based on the selected month from a slicer.
- Each day on the calendar is color-coded to represent sales volume, with darker shades indicating higher sales.
- Tooltips display detailed metrics (Sales, Orders, Quantity) when hovering over a specific day.

### 5. Sales Analysis by Weekdays and Weekends:
- Segment sales data into weekdays and weekends to analyze performance variations.
- Provide insights into whether sales patterns differ significantly between weekdays and weekends.

### 6. Sales Analysis by Store Location:
- Visualize sales data by different store locations.
- Include month-over-month (MoM) difference metrics based on the selected month in the slicer.
- Highlight MoM sales increase or decrease for each store location to identify trends.

### 7. Daily Sales Analysis with Average Line:
- Display daily sales for the selected month with a line chart.
- Incorporate an average line on the chart to represent the average daily sales.
- Highlight bars exceeding or falling below the average sales to identify exceptional sales days.

### 8. Sales Analysis by Product Category:
- Analyze sales performance across different product categories.
- Provide insights into which product categories contribute the most to overall sales.

### 9. Top 10 Products by Sales:
- Identify and display the top 10 products based on sales volume.
- Allow users to quickly visualize the best-performing products in terms of sales.

### 10. Sales Analysis by Days and Hours:
- Utilize a heat map to visualize sales patterns by days and hours.
- Implement tooltips to display detailed metrics (Sales, Orders, Quantity) when hovering over a specific day-hour.

## 2. PREPARE

**Data Storage:**
The data is stored in Excel format and contains records for the month of May 2023. It includes key metrics like sales, quantity sold, orders, and transaction IDs.

**Data Organization:**
The dataset consists of the following:
- **Sales Data**: Daily sales, order counts, and quantities sold.
- **Product Categories**: Information on the type of product sold.
- **Store Locations**: Store-specific performance data.

**Tools Used:**
- **Power BI**: The primary tool for creating the dashboard and visualizations.

## 3. PROCESS

**Data Cleaning & Transformation:**
- Removed duplicate and incomplete entries.
- Standardized date formats.
- Aggregated sales data by day, week, product type, and store location.
- Created necessary calculated columns and measures using DAX formulas.

**Key Data Fields:**
- **Date**: Transaction date.
- **Product Category**: Product type (coffee, tea, bakery items, etc.).
- **Store Location**: The store where the transaction occurred.
- **Sales Amount**: Revenue generated from each transaction.
- **Quantity Sold**: The number of units sold.
- **Order Count**: Number of orders.

## 4. ANALYZE

**Key Metrics and Formulas:**

1. **Total Sales**: The sum of sales revenue for the selected period.
   - SUM(Transactions[Sales])

2. **Total Orders**: The total number of distinct orders placed.
   - DISTINCTCOUNT(Transactions[transaction_id])

3. **Total Quantity Sold**: The total number of units sold.
   - SUM(Transactions[Transaction_Qty])

4. **Average Sales**: The average daily sales amount.
   - AVERAGEX(ALLSELECTED(Transactions[transaction_date]), 'Date Table'[Total Sales])

5. **Previous Month Sales**: Sales in the previous month.
   - CALCULATE('Transactions'[CM], DATEADD('Date Table'[Date], -1, MONTH))

6. **Previous Month Orders**: Number of orders in the previous month.
   - CALCULATE('Transactions'[CM Orders], DATEADD('Date Table'[Date], -1, MONTH))

7. **Previous Month Quantity Sold**: Quantity sold in the previous month.
   - CALCULATE('Transactions'[CM Qty], DATEADD('Date Table'[Date], -1, MONTH))

8. **Current Month Sales**: Sales for the selected month.
   - DAX
     VAR selected_month = SELECTEDVALUE('Date Table'[Month])
     RETURN TOTALMTD(
       CALCULATE(SUM(Transactions[Sales]), 'Date Table'[Month] = selected_month),
       'Date Table'[Date]
     )
     

## 5. SHARE

https://github.com/user-attachments/assets/82ddf263-4026-4875-b754-b7196c77e3f6

<br>
Check Out the Live Dashboard [here](https://app.powerbi.com/links/usUAZjSUc1?ctid=3cc54fba-ae76-46dc-9e2d-7250294bedc4&pbi_source=linkShare).


## 6. ACT

**Recommendations**

Target Weekends for Sales Growth:
The analysis shows that weekends contribute 33% of revenue (April) compared to 26% in March, indicating that weekend sales are growing. To capitalize on this, consider implementing weekend promotions or special deals to drive even more foot traffic and increase weekend revenue further.

Optimize Product Offerings:
Coffee is the best-selling product category, but Bakery items saw the highest growth (+31.7% in March and +20% in April). Promoting bakery items with coffee as a combo deal could further boost sales in this growing category. Additionally, increasing focus on hot beverages like Barista Espresso and Brewed Chai Tea, which are also growing, can help drive more profits.

Expand Sales in Lower Performing Store Locations:
While Hell’s Kitchen and Astoria stores are performing well, the Lower Manhattan store has the lowest revenue among the three. Implement targeted marketing campaigns or offer location-based deals to improve sales in that region.

Maximize Peak Sales Hours:
heatmap shows that 12 PM to 4 PM is the busiest time for sales. Capitalize on this by offering promotions or loyalty programs during slower hours (such as early morning or after 5 PM) to encourage more traffic throughout the day and balance sales distribution.
