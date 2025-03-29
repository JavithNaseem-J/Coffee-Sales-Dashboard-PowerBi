# Coffee Shop Sales Analysis Dashboard


## Overview
The Coffee Shop Sales Analysis Dashboard is a Power BI project that visualizes sales data for a local coffee shop chain. It focuses on key performance indicators (KPIs) such as total sales, total orders, and total quantity sold, with detailed breakdowns by product category, product type, store location, and sales trends over time. The dashboard is designed to help stakeholders understand sales patterns, identify top-performing products, and optimize business operations.


## Dataset
- **transaction_id**: Unique identifier for each transaction.
- **transaction_date**: Date of the transaction.
- **transaction_time**: Time of the transaction.
- **transaction_qty**: Quantity of items sold in the transaction.
- **store_id**: Unique identifier for the store.
- **store_location**: Location of the store.
- **product_id**: Unique identifier for the product.
- **unit_price**: Price per unit of the product.
- **product_category**: Category of the product.
- **product_type**: Type of product within the category.
- **product_detail**: Specific details of the product.




### DAX Forumlas
- **Key Metrics and Formulas**:
  - **Total Sales**: Sum of sales revenue for the selected period.
    - Formula: `SUM(Transactions[Sales])`
  - **Total Orders**: Total number of distinct orders placed.
    - Formula: `DISTINCTCOUNT(Transactions[transaction_id])`
  - **Total Quantity Sold**: Total number of units sold.
    - Formula: `SUM(Transactions[Transaction_Qty])`
  - **Average Sales**: Average daily sales amount.
    - Formula: `AVERAGEX(ALLSELECTED(Transactions[transaction_date]), 'Date Table'[Total Sales])`
  - **Previous Month Sales**: Sales in the previous month.
    - Formula: `CALCULATE('Transactions'[CM], DATEADD('Date Table'[Date], -1, MONTH))`
  - **Previous Month Orders**: Number of orders in the previous month.
    - Formula: `CALCULATE('Transactions'[CM Orders], DATEADD('Date Table'[Date], -1, MONTH))`
  - **Previous Month Quantity Sold**: Quantity sold in the previous month.
    - Formula: `CALCULATE('Transactions'[CM Qty], DATEADD('Date Table'[Date], -1, MONTH))`
  - **Current Month Sales**: Sales for the selected month.
    - Formula: 
      ```
      DAX VAR selected_month = SELECTEDVALUE('Date Table'[Month])
      RETURN TOTALMTD(
        CALCULATE(SUM(Transactions[Sales]), 'Date Table'[Month] = selected_month),
        'Date Table'[Date]
      )
      ```

## Prerequisites
To use this Power BI dashboard, you need the following:
- **Power BI Desktop**: Download and install the latest version from [Microsoft's official website](https://powerbi.microsoft.com/en-us/downloads/).
- **Dataset**: A CSV or Excel file containing coffee shop sales data with columns similar to those described in the [Dataset](#dataset) section.
- **Basic Power BI Knowledge**: Familiarity with Power BI Desktop, including data import, DAX calculations, and dashboard creation.

## Installation
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/coffee-shop-sales-dashboard.git
   cd coffee-shop-sales-dashboard
   ```

2. **Open the Power BI File**:
   - Open `CoffeeShopSalesDashboard.pbix` in Power BI Desktop.

3. **Connect Your Dataset**:
   - If you have your own dataset, import it into Power BI Desktop:
     - Go to `Home` > `Get Data` > Select your data source (e.g., Excel, CSV).
     - Load your dataset and map the columns to the existing data model in the `.pbix` file.
   - Update the data connections if necessary.

4. **Refresh the Dashboard**:
   - Click `Refresh` in Power BI Desktop to update the visuals with your data.

## Usage
1. **Open the Dashboard**:
   - Launch Power BI Desktop and open `CoffeeShopSalesDashboard.pbix`.

2. **Interact with the Dashboard**:
   - Use the **Month** dropdown to select a specific month (default: May 2023).
   - Explore the visuals to analyze sales trends, product performance, and store comparisons.
   - Hover over charts to see detailed tooltips with sales metrics.

3. **Export or Share**:
   - Export the dashboard as a PDF or PowerPoint for presentations: `File` > `Export`.
   - Publish to Power BI Service to share with your team: `Home` > `Publish`.

## Dashboard Components
The dashboard includes the following components:
- **Month Filter**: Dropdown to select the analysis period.
- **KPIs**:
  - Total sales, orders, and quantity sold with month-over-month comparisons.
- **Sales by Date**: Line chart showing daily sales trends with an average sales line.
- **Sales by Week**: Donut chart showing the split between weekdays and weekends.
- **Sales by Product Category**:
  - Bar chart displaying sales across categories like coffee, tea, bakery, etc.
- **Sales by Product Type**:
  - Detailed breakdown of sales by specific product types.
- **Sales by Store Location**:
  - Comparison of sales across different store locations with month-over-month differences.
- **Sales by Day and Hour**:
  - Heatmap showing sales patterns across days of the week and hours of the day.



## Dashboard

https://github.com/user-attachments/assets/82ddf263-4026-4875-b754-b7196c77e3f6

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
