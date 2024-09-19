Here’s a structured README file that you can use for your GitHub repository based on your SQL analysis project:

---

# Amazon Sales Data Analysis

### Overview

This repository contains SQL queries and analyses based on an Amazon sales data spreadsheet. The goal of this project is to perform an in-depth analysis of product-related data to gain insights into product ratings, discounts, and reviews.

### Table of Contents

1. [Instructions](#instructions)
2. [Queries and Answers](#queries-and-answers)
3. [Results and Insights](#results-and-insights)
4. [Conclusion](#conclusion)

### Instructions

- Open the provided spreadsheet and review the data in each sheet carefully.
- Use the SQL queries provided in the `queries.sql` file to extract insights from the data.
- Compile the answers in a well-organized PDF document.
- Ensure all calculations and queries are accurate.
- Submit your document via Google Classroom.
- Create a PowerPoint report of this analysis and post it on LinkedIn. Include a screenshot of the post in the classroom.

### Queries and Answers

Below are the SQL queries developed for this analysis:

```sql
1. -- List all products with their product_id, product_name, and category
SELECT product_id, product_name, category FROM products;

2. -- Display all columns for products that have a rating of 4.0 or higher
SELECT * FROM products WHERE rating >= 4.0;

3. -- List products in the Computers & Accessories category
SELECT * FROM products WHERE category = 'Computers & Accessories';

4. -- Find all products where the about_product column contains the word 'durable'
SELECT * FROM products WHERE about_product LIKE '%durable%';

5. -- Count the total number of products in the dataset
SELECT COUNT(*) AS total_products FROM products;

6. -- Find the average rating of all products
SELECT AVG(rating) AS average_rating FROM products;

7. -- List the top 5 highest-rated products sorted in descending order
SELECT * FROM products ORDER BY rating DESC LIMIT 5;

8. -- List all products along with the number of reviews
SELECT product_id, product_name, review_count FROM products;

9. -- Find products that have the same rating and belong to the same category
SELECT p1.product_id, p1.product_name, p1.category, p1.rating 
FROM products p1
JOIN products p2 ON p1.rating = p2.rating AND p1.category = p2.category AND p1.product_id <> p2.product_id;

10. -- Categorize products based on their rating using a CASE statement
SELECT product_id, product_name, 
   CASE
      WHEN rating >= 4.5 THEN 'Excellent'
      WHEN rating >= 4.0 THEN 'Good'
      ELSE 'Average'
   END AS rating_category
FROM products;

11. -- Add a new column discount_amount that calculates the difference between actual_price and discounted_price
ALTER TABLE products ADD COLUMN discount_amount DECIMAL(10, 2);
UPDATE products SET discount_amount = actual_price - discounted_price;

12. -- Find the product with the highest discount_percentage
SELECT *, (actual_price - discounted_price) / actual_price * 100 AS discount_percentage 
FROM products ORDER BY discount_percentage DESC LIMIT 1;

13. -- Create a view named HighRatingProducts for products with a rating of 4.5 and above
CREATE VIEW HighRatingProducts AS 
SELECT * FROM products WHERE rating >= 4.5;

14. -- Find the category with the highest average rating for products
SELECT category, AVG(rating) AS average_rating
FROM products
GROUP BY category
ORDER BY average_rating DESC
LIMIT 1;

15. -- Find pairs of products from the same category with one having a higher rating than the other
SELECT p1.product_id AS product_id_1, p1.product_name AS product_name_1, p1.rating AS rating_1, 
       p2.product_id AS product_id_2, p2.product_name AS product_name_2, p2.rating AS rating_2
FROM products p1
JOIN products p2 ON p1.category = p2.category AND p1.rating > p2.rating;
```

### Results and Insights

- A comprehensive analysis of the products revealed various insights, including the distribution of product ratings and the effectiveness of discounts.
- The creation of a view for high-rated products allows for easier access to quality items for consumers.
- Comparing products within the same category highlights competitive advantages based on ratings.

### Conclusion

This project demonstrates the power of SQL in analyzing product data within a retail context. The queries included provide an extensive overview of how to interact with and extract meaningful insights from sales data.

Feel free to explore the queries and adapt them for further analysis or use.

### License

This project is licensed under the MIT License - see the LICENSE file for details.

---

Make sure to replace any placeholders or modify details as necessary. You can then add this README file to your GitHub repository for clarity and to guide any readers or collaborators who may view your project. 
