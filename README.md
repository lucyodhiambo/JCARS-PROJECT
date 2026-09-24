# JCars Sales Analytics — Power BI & PostgreSQL

## Project Overview

JCars Sales Analytics is a business intelligence project that analyzes vehicle sales data using **PostgreSQL on Aiven, DBeaver**.

The project transforms raw JCars sales data into a structured database and interactive Power BI dashboard. The dashboard provides insights into revenue, gross profit, vehicle performance, sales representatives, branches, regions, payment methods, and delivery performance.

## Project Objective

The objective of this project is to:

* Analyze JCars sales performance.
* Identify the vehicles and vehicle categories generating the most revenue.
* Evaluate gross profit and gross profit margin.
* Compare sales performance across branches and regions.
* Analyze sales representatives and lead sources.
* Examine payment methods and payment status.
* Analyze delivery performance and delivery times.
* Build an interactive Power BI dashboard to support data-driven business decisions.

## Technology Stack

* **PostgreSQL** — database and data storage
* **Aiven** — cloud-hosted PostgreSQL database
* **DBeaver** — database management
* **CSV** — original source data

## Data Pipeline

JCars CSV- Data Cleaning- Star Schema - Power BI - Interactive Dashboard

## Data Import into Aiven

The JCars data was imported into a PostgreSQL database hosted on Aiven.

DBeaver was used as the database management and development environment. The cleaned JCars data was loaded into PostgreSQL and organized into fact and dimension tables.

The database follows a **star schema** structure, with the main sales fact table connected to supporting dimension tables.

### Main Fact Table

 Facts_Jcar_sales

### Dimension Tables

* Customer
* Vehicle
* Date
* Location

The star schema makes it easier to analyze sales data while maintaining clear relationships between the transactional data and descriptive attributes.

## Data Cleaning and Preparation

Several data-quality issues were addressed before analysis.

### Date Cleaning

The source data contained different date formats, including Excel serial numbers and text-based dates.

The dates were transformed into valid date values so they could be used for time-based analysis.

### Monetary Data Cleaning

Currency values contained formatting such as:

* KES
* KSh
* commas
* values expressed using M

These values were cleaned and converted into appropriate numeric data types.

### Data Types

Columns were assigned appropriate data types, including:

* Date → Date
* Revenue → Decimal number
* Unit Cost → Decimal number
* Selling Price → Decimal number
* Units Sold → Whole number
* IDs → appropriate key/data types

## Measures and Calculations

Several DAX measures were created to support the dashboard.

### Total Revenue
Total Revenue =
SUM(Facts_Jcar_sales[Revenue Recorded clean])

### Total Units Sold
Total Units Sold =
SUM(Facts_Jcar_sales[Units Sold])

### Total Orders
Total Orders =
DISTINCTCOUNT(Facts_Jcar_sales[Order ID])

### Total Gross Profit
Total Gross Profit =
SUM(Facts_Jcar_sales[Revenue Recorded clean])
    - SUM(Facts_Jcar_sales[Unit Cost Clean])

### Gross Profit Margin
Gross Profit Margin =
DIVIDE(
    [Total Gross Profit],
    [Total Revenue],
    0
)

### Customer Count
Customer Count =
DISTINCTCOUNT(Facts_Jcar_sales[CustomerID])

### Revenue per Customer
Revenue per Customer =
DIVIDE(
    [Total Revenue],
    [Customer Count],
    0
)

### Delivery Days

A calculated column was created to determine the number of days between order and delivery.
Delivery Days =
DATEDIFF(
    Facts_Jcar_sales[Order Date],
    Facts_Jcar_sales[Delivery Date],
    DAY
)

### Average Delivery Time
Average Delivery Time =
AVERAGE(Facts_Jcar_sales[Delivery Days])

## Dashboard Visuals

The Power BI dashboard contains visuals designed to answer key business questions.

### KPI Cards

* Total Revenue
* Total Units Sold
* Total Orders
* Total Gross Profit
* Gross Profit Margin

### Sales Analysis

* Revenue by Car Make
* Units Sold by Car Model
* Revenue by Vehicle Type
* Units Sold by Vehicle Type

### Branch and Regional Analysis

* Revenue by Branch
* Revenue by Region/County
* Sales performance across locations

### Sales Representative Analysis

* Revenue by Sales Representative
* Units Sold by Sales Representative

### Customer and Lead Source Analysis

* Revenue by Lead Source
* Customer Count
* Revenue per Customer

### Time Analysis

* Monthly Revenue Trend
* Monthly Gross Profit Trend
* Monthly Units Sold Trend

### Payment Analysis

* Revenue by Payment Method
* Revenue by Payment Status
* Orders by Payment Status

### Delivery Analysis

* Orders by Delivery Status
* Average Delivery Time by Region
* Average Delivery Time by Branch
* Average Delivery Time by Car Make

### Interactive Controls

The dashboard also includes slicers that allow users to filter the analysis by relevant dimensions such as:

* Month
* Vehicle
* Branch
* Region
* Payment Status
* Delivery Status

## Key Insights

The dashboard enables JCars to identify:

* Which vehicle makes generate the highest sales revenue.
* Which vehicle models have the highest unit sales.
* Which vehicle types contribute most to overall performance.
* Which branches and regions generate stronger sales.
* Which sales representatives generate higher revenue and unit sales.
* Which lead sources generate valuable customers.
* How revenue and gross profit change over time.
* Which payment methods contribute the most revenue.
* The distribution of orders across payment statuses.
* Which delivery statuses account for the largest number of orders.
* How delivery times vary across regions, branches, and vehicle makes.

## Recommendations

Based on the dashboard analysis, JCars can use the findings to:

1. **Prioritize high-performing vehicles**
   Maintain appropriate inventory levels for vehicle makes and models that consistently generate strong sales.

2. **Improve branch performance**
   Investigate differences between branches and identify practices used by stronger-performing locations.

3. **Optimize sales activities**
   Use sales-representative and lead-source analysis to understand which sales channels generate valuable business.

4. **Monitor profitability**
   Track gross profit and gross profit margin alongside revenue rather than relying on sales revenue alone.

5. **Improve delivery operations**
   Monitor delivery times by region, branch, and vehicle type to identify areas where logistics performance can be improved.

6. **Monitor payment performance**
   Track payment status and payment methods to identify outstanding payments and understand customer payment behavior.

## Conclusion

The JCars Sales Analytics project demonstrates how raw sales data can be transformed into an analytical solution using **PostgreSQL, Aiven, DBeaver, and Power BI**.

The combination of a structured star-schema database, SQL-based data management, DAX calculations, and interactive Power BI visualizations provides a foundation for analyzing sales, profitability, customer behavior, and operational performance.

## practical skills 
**data cleaning, SQL, database design, data modeling, DAX, Power BI visualization, and business intelligence**.
