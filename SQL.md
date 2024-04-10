### What's SQL?

SQL (Structured Query Language), ilişkisel veritabanlarını yönetmek için kullanılan bir dildir. SQL'in iki temel alt kümesi bulunur: 
1. **DDL (Data Definition Language - Veri Tanımlama Dili)**
2. **DML (Data Manipulation Language - Veri İşleme Dili)**

<br>

**DDL (Veri Tanımlama Dili):**

* **Veritabanı yapısını yönetir.**
* Tablolar oluşturma, silme, değiştirme gibi işlemleri gerçekleştirir.
* Veritabanı şemasını tanımlar.

**DDL komutları şunları içerir:**

* **CREATE:** Yeni tablolar, dizinler, görünümler ve kullanıcılar oluşturur.
* **ALTER:** Mevcut veritabanı nesnelerinin yapısını değiştirir.
* **DROP:** Tablolar, dizinler, görünümler ve kullanıcıları siler.
* **GRANT:** Kullanıcılara belirli izinler verir.
* **REVOKE:** Kullanıcılardan izinleri kaldırır.

**Örnek DDL komutu:**

```sql
CREATE TABLE customers (
  id INT PRIMARY KEY AUTO_INCREMENT,
  name VARCHAR(255) NOT NULL,
  email VARCHAR(255) UNIQUE
);
```


**DML (Veri İşleme Dili):**

* **Veritabanındaki verileri manipüle eder.**
* Verilerin eklenmesi, silinmesi, güncellenmesi ve sorgulanması gibi işlemleri gerçekleştirir.

**DML komutları şunları içerir:**

* **INSERT:** Veritabanına yeni kayıtlar ekler.
* **UPDATE:** Mevcut kayıtların verilerini değiştirir.
* **DELETE:** Veritabanından kayıtları siler.
* **SELECT:** Veritabanından kayıtları sorgular ve sonuçları döndürür.

**Örnek DML komutu:**

```sql
INSERT INTO customers (name, email) VALUES ("Alice Smith", "alice@email.com");

UPDATE customers SET name = "John Doe" WHERE id = 1;

DELETE FROM customers WHERE email = "jane@email.com";

SELECT * FROM customers;  -- Tüm kayıtları seç
```

### WHERE, ORDER BY, GROUP BY, HAVING 

**WHERE:**

* Filters data based on a condition. Only rows meeting the condition are returned.

```sql
SELECT * FROM users WHERE age >= 18;  -- Select users 18 or older
```

**ORDER BY:**

* Sorts the result set based on one or more columns. Specify ASC (ascending) or DESC (descending).

```sql
SELECT * FROM products ORDER BY price ASC;   -- Order products by price (cheapest first)
SELECT * FROM orders ORDER BY order_date DESC; -- Order orders by date (newest first)
```

**GROUP BY:**

* Groups data based on one or more columns. Often used with aggregate functions (COUNT, SUM, AVG).

```sql
SELECT category, COUNT(*) AS product_count
FROM products
GROUP BY category;  -- Count products by category
```

**HAVING:**

* Filters groups after `GROUP BY`. Works on groups, not individual rows.

```sql
SELECT country, COUNT(*) AS customer_count
FROM customers
GROUP BY country
HAVING customer_count > 100;  -- Show countries with over 100 customers
```

**Remember:**

* `WHERE` filters before grouping (`GROUP BY`).
* `HAVING` filters groups after grouping.


### Functions
These are all functions commonly used in SQL for data manipulation and retrieval. Here's a breakdown of each:

**String Functions:**

* **LOWER(string):** Converts a string to lowercase.
* **UPPER(string):** Converts a string to uppercase.

**Example:**

```sql
SELECT UPPER(name), LOWER(email) FROM users;
```

**Aggregate Functions:**

* **COUNT(*):** Counts the number of rows (all columns) in a table or result set.
* **COUNT(column_name):** Counts the number of non-null values in a specific column.
* **MAX(column_name):** Returns the largest value in a column.
* **MIN(column_name):** Returns the smallest value in a column.
* **SUM(column_name):** Calculates the sum of all values in a column (numerical data only).
* **AVG(column_name):** Calculates the average of all values in a column (numerical data only).

**Example:**

```sql
SELECT COUNT(*), SUM(price) FROM products;  -- Count products and total price
SELECT MAX(salary) FROM employees;  -- Find highest salary
```

**Date/Time Function:**

* **EXTRACT(part FROM datetime_expression):** Extracts a specific part from a date or time value. Valid parts include `YEAR`, `MONTH`, `DAY`, `HOUR`, `MINUTE`, `SECOND`, etc.

**Example:**

```sql
SELECT EXTRACT(YEAR FROM hire_date) AS hire_year FROM employees;
```

**Important Notes:**

* String functions are often used to manipulate text data for searching, sorting, or formatting purposes.
* Aggregate functions are typically used with the `GROUP BY` clause to summarize data within groups.
* The `EXTRACT` function is helpful for extracting specific date or time components.

## Arithmetical and Logical Operators in SQL

SQL offers both **arithmetical operators** for performing calculations and **logical operators** for combining conditions within your queries.

**Arithmetical Operators:**

These operators allow you to perform mathematical calculations on numerical data in your tables.

* **+ (Addition):** Adds two numbers.
* **- (Subtraction):** Subtracts one number from another.
* **\* (Multiplication):** Multiplies two numbers.
* **/ (Division):** Divides one number by another.
* **% (Modulo):** Returns the remainder after division.

**Example:**

```sql
SELECT product_id, price * quantity AS total_price
FROM order_items;  -- Calculate total price (price * quantity)
SELECT age - YEAR(CURDATE()) AS current_age
FROM users;  -- Calculate current age (age - current year)
```

**Logical Operators:**

These operators help you combine conditions and refine your queries based on multiple criteria.

* **AND:** Both conditions must be true for the overall condition to be true.
* **OR:** At least one condition must be true for the overall condition to be true.
* **NOT:** Inverts the truth value of a condition (true becomes false, false becomes true).

**Example:**

```sql
SELECT * FROM products WHERE price > 100 AND category = "Electronics";  -- Products over $100 in "Electronics"
SELECT * FROM users WHERE age >= 18 OR is_admin = 1;  -- Users 18 or older OR admins
SELECT * FROM orders WHERE shipped = 0 AND order_date > DATE_SUB(CURDATE(), INTERVAL 7 DAY);  -- Unshipped orders in the last week
```

**Important Notes:**

* Arithmetical operators typically have higher precedence than logical operators in SQL expressions. Use parentheses for proper evaluation order if needed.
* Logical operators are essential for creating complex and targeted SQL queries.


By understanding these operators, you can manipulate numerical data, combine conditions, and retrieve the specific information you need from your database.

### Other operators

These operators are commonly used in SQL's `WHERE` clause to filter data based on specific criteria. Here's a breakdown of each:

**BETWEEN:**

* Used to check if a value falls within a specified range (inclusive).

```sql
SELECT * FROM products WHERE price BETWEEN 50 AND 100;  -- Products priced between $50 and $100
SELECT * FROM orders WHERE order_date BETWEEN '2024-04-01' AND '2024-04-10';  -- Orders placed between April 1st and 10th, 2024
```

**IN:**

* Checks if a value matches one or more values from a specified list.

```sql
SELECT * FROM customers WHERE country IN ('USA', 'Canada', 'Mexico');  -- Customers from USA, Canada, or Mexico
SELECT * FROM products WHERE category IN ('Electronics', 'Books', 'Toys');  -- Products in these categories
```

**LIKE:**

* Performs pattern matching on text data. You can use wildcards (`%`) to match any sequence of characters or underscores (`_`) to match a single character.

```sql
SELECT * FROM users WHERE name LIKE '%Smith';  -- Names containing "Smith"
SELECT * FROM products WHERE product_name LIKE 'Headset%';  -- Products starting with "Headset"
SELECT * FROM emails WHERE subject LIKE 'Meeting _%';  -- Emails with subjects starting with "Meeting " followed by any word
```

**IS NULL:**

* Checks if a column value is null (missing or undefined).

```sql
SELECT * FROM customers WHERE email IS NULL;  -- Customers with no email address
SELECT * FROM orders WHERE shipped_date IS NOT NULL;  -- Orders that have been shipped
```

**Important Notes:**

* `BETWEEN` is useful for filtering data within a specific range.
* `IN` allows you to check against a predefined set of values.
* `LIKE` provides flexibility for pattern matching in text searches.
* `IS NULL` helps identify missing data in your tables.

These operators enhance your ability to filter and retrieve specific data in your SQL queries. 