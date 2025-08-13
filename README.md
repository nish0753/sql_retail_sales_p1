# sql_retail_sales_p1

This repository contains SQL scripts for analyzing and managing retail sales data. It is designed for business intelligence, reporting, and data-driven insights in retail operations.

## Features

- Schema creation and data cleaning for retail sales
- Data exploration and business key problem-solving
- Analytical queries for common retail metrics
- Modular SQL for easy extension

## SQL Questions Included

1. **Total Sales Count**
   ```sql
   SELECT COUNT(*) AS total_sale FROM retail_sales;
   ```
2. **Unique Customer Count**
   ```sql
   SELECT COUNT(DISTINCT customer_id) as unique_customer FROM retail_sales;
   ```
3. **Distinct Product Categories**
   ```sql
   SELECT DISTINCT category as category FROM retail_sales;
   ```
4. **Sales on a Specific Day**
   ```sql
   SELECT * FROM retail_sales WHERE sale_date = '2022-11-05';
   ```
5. **Clothing Sales (Quantity > 4 in Nov 2022)**
   ```sql
   SELECT *
   FROM retail_sales
   WHERE category = 'Clothing'
     AND TO_CHAR(sale_date,'YYYY-MM') = '2022-11'
     AND quantity >= 4;
   ```
6. **Total Sale by Category**
   ```sql
   SELECT category, SUM(total_sale) AS total_sale
   FROM retail_sales
   GROUP BY category;
   ```
7. **Average Age by Category**
   ```sql
   SELECT category, AVG(age) AS avg_age
   FROM retail_sales
   GROUP BY category;
   ```
8. **High Value Transactions (Total Sale > 1000)**
   ```sql
   SELECT *
   FROM retail_sales
   WHERE total_sale > 1000;
   ```
9. **Transactions by Gender and Category**
   ```sql
   SELECT gender, category, COUNT(*) AS total
   FROM retail_sales
   GROUP BY gender, category;
   ```
10. **Top 10 Customers by Total Sale**
    ```sql
    SELECT customer_id, SUM(total_sale) AS total_sale
    FROM retail_sales
    GROUP BY customer_id
    ORDER BY total_sale DESC
    LIMIT 10;
    ```
11. **Unique Customers by Category**
    ```sql
    SELECT category, COUNT(DISTINCT customer_id) AS unique_customers
    FROM retail_sales
    GROUP BY category;
    ```
12. **Orders by Shift (Morning, Afternoon, Evening)**
    ```sql
    SELECT
      CASE
        WHEN sale_time BETWEEN '06:00:00' AND '12:00:00' THEN 'Morning'
        WHEN sale_time BETWEEN '12:01:00' AND '18:00:00' THEN 'Afternoon'
        ELSE 'Evening'
      END AS shift,
      COUNT(*) AS orders
    FROM retail_sales
    GROUP BY shift;
    ```

## Getting Started

1. Clone this repository:
   ```bash
   git clone https://github.com/nish0753/sql_retail_sales_p1.git
   ```
2. Review and run `sql_query_p1.sql` against your retail sales database.

## Author

- [nish0753](https://github.com/nish0753)

## License

Not specified

---

## Summary of the Code

The code in this repository establishes a retail sales database schema, cleanses the data by removing incomplete records, and explores key metrics such as total sales, customer counts, and product categories. It provides a series of SQL queries to analyze sales by date, category, customer, and time of day. The queries help identify trends, top-performing categories and customers, and segment sales data for deeper business insights. This makes the repository a valuable resource for retail analytics and performance tracking.