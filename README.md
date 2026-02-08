# Analyzing-a-retail-database-to-identify-high-performing-regions-and-personalized-product-offerings
This project focuses on extracting actionable business insights from a relational database. By utilizing intermediate SQL techniques—including Joins, Aggregations, and Grouping—I answered key stakeholder questions regarding regional performance and product sales.

# Database Schema

The analysis was performed on a mock retail database containing three primary tables:

Customers: Demographic information and unique IDs.

Retail_sales_dataset: Sales data including dates and dollar amounts.

Sample_superstore: Order information of customers.

Business Questions & SQL Solutions

# 1. Which region has the highest sales?

To solve this, I joined the sales data with geographical regions and aggregated the total revenue.


SELECT 
    *
FROM
    sample_superstore;
SELECT 
    `Customer ID`
FROM
    sample_superstore;
SELECT 
    sample_superstore.`Order ID`,
    sample_superstore.`Customer Name`,
    sample_superstore.Sales,
    customers.CustomerID
FROM
    sample_superstore
        LEFT JOIN
    customers ON sample_superstore.`Customer ID` = customers.CustomerID;
/*Highest sales by region*/
SELECT 
    Region, COUNT(Sales)
FROM
    sample_superstore
GROUP BY Region
ORDER BY COUNT(Sales) DESC;

# Insight: The West Region is currently the top performer. This suggests that marketing efforts are successfully converting in this territory.

# 2. Which product category has the highest sales?

This query identifies our "VIP" product by calculating the total spend per product.


SELECT 
    *
FROM
    retail_sales_dataset;
SELECT 
    `Customer ID`
FROM
    retail_sales_dataset;
/*Highest sales by product category*/
SELECT 
    SUM(`Total Amount`), `Product Category`
FROM
    retail_sales_dataset
GROUP BY `Product Category`
ORDER BY SUM(`Total Amount`) DESC;

# Insight: The top 5 products account for a significant portion of total revenue. I recommend a targeted loyalty program for this specific segment to increase retention.

# Skills Demonstrated
Data Aggregation: Using SUM(), COUNT(), and GROUP BY to summarize thousands of rows.

Relational Mapping: Utilizing INNER JOIN to connect disparate tables into a unified view.

Data Sorting: Applying ORDER BY and LIMIT to find top-tier performers and outliers.



# About the Developer

I am a developing Data Analyst currently mastering the art of SQL. This project represents Week 4 of my journey, where I moved from learning basic commands to solving real-world business puzzles. 

What I learned during this project:
How to connect different data tables using JOINs (like pieces of a puzzle).
How to use GROUP BY to turn a giant list of numbers into a clear summary.
How to visualize a database "map" using ER Diagrams.

I love turning messy data into clear answers!
