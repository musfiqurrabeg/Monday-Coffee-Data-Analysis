# Coffee Market Analysis with PostgreSQL

## Project Overview
This project analyzes coffee consumption, sales, and market potential across multiple cities using PostgreSQL. The dataset includes information on city populations, sales transactions, product data, and more. Based on the analysis, the project provides actionable insights and recommendations for optimizing coffee business operations, including identifying top cities for potential store openings.

## Features
1. **Coffee Consumers Count**
   - Estimates the number of coffee consumers in each city (25% of the population).

2. **Total Revenue from Coffee Sales**
   - Calculates total revenue generated from coffee sales in the last quarter of 2023.

3. **Sales Count for Each Product**
   - Counts the total units sold for each coffee product.

4. **Average Sales Amount per City**
   - Computes the average sales amount per customer in each city.

5. **City Population and Coffee Consumers**
   - Lists cities along with their population and estimated coffee consumers.

6. **Top Selling Products by City**
   - Identifies the top 3 selling coffee products in each city based on sales volume.

7. **Customer Segmentation by City**
   - Analyzes the number of unique customers in each city who purchased coffee products.

8. **Average Sale vs Rent**
   - Compares average sales per customer with average rent per customer in each city.

9. **Monthly Sales Growth**
   - Tracks the percentage growth or decline in sales across months.

10. **Market Potential Analysis**
    - Identifies the top 3 cities with the highest sales potential and provides detailed insights.

## Recommendations
Based on the analysis, the following cities are recommended for new store openings:

1. **Pune**
   - Low average rent per customer.
   - Highest total revenue.
   - High average sales per customer.

2. **Delhi**
   - Largest estimated coffee consumer base (7.7 million).
   - Highest number of customers (68).
   - Affordable average rent per customer (330).

3. **Jaipur**
   - Highest number of customers (69).
   - Very low average rent per customer (156).
   - Strong average sales per customer (11.6k).

## Getting Started

### Prerequisites
- PostgreSQL (version 13 or later).
- SQL client (e.g., pgAdmin, DBeaver).

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/coffee-market-analysis.git
   cd coffee-market-analysis
   ```

2. Set up the database:
   - Create a PostgreSQL database.
   - Run `Schemas.sql` to set up the database schema.
   - Run `pgsql_query.sql` to insert sample data and execute queries.

3. Execute the queries:
   - Use your preferred SQL client to run the provided queries for analysis.

### File Structure
- `Schemas.sql`: Contains the database schema definitions.
- `pgsql_query.sql`: Includes the SQL queries for data analysis.
- `README.md`: Project documentation.

## Key SQL Queries
- **Calculate Estimated Coffee Consumers**:
  ```sql
  SELECT city_name, population, (population * 0.25) AS estimated_coffee_consumers
  FROM cities;
  ```

- **Total Revenue in Q4 2023**:
  ```sql
  SELECT SUM(sales_amount) AS total_revenue
  FROM sales
  WHERE sale_date BETWEEN '2023-10-01' AND '2023-12-31';
  ```

- **Top 3 Selling Products by City**:
  ```sql
  SELECT city_name, product_name, SUM(quantity_sold) AS total_sold
  FROM sales
  JOIN products ON sales.product_id = products.product_id
  GROUP BY city_name, product_name
  ORDER BY city_name, total_sold DESC
  LIMIT 3;
  ```

## Insights and Visualizations
- The analysis uncovers patterns in consumer behavior, sales trends, and city-wise performance.
- Visualizations can be generated using tools like Tableau or Power BI for enhanced insights.

## Future Scope
- Integrate real-time data pipelines for dynamic analysis.
- Incorporate machine learning models for predictive analytics.
- Expand the analysis to include global data.

## Contributing
Contributions are welcome! Please open an issue or submit a pull request for any changes.

## License
This project is licensed under the MIT License. See `LICENSE` for details.

## Contact
For queries, feel free to reach out:
- Name: Your Name
- Email: your.email@example.com
- GitHub: [your-username](https://github.com/your-username)

---
**Happy Coding!**
