🔍 What is an INNER JOIN?
An INNER JOIN in SQL is used to retrieve records that have matching values in both tables involved in the join. It returns only the rows where there is a match.
If no match is found between the two tables, the row is excluded from the result.

🧠 Basic Syntax of INNER JOIN
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column_name = table2.column_name;

📘 Real-world Example
Let’s say we have two tables:
🧾 Table: Customers
CustomerID	CustomerName
1	Alice
2	Bob
3	Charlie
📦 Table: Orders
OrderID	CustomerID	Product
101	1	Laptop
102	3	Phone
103	4	Tablet

✅ INNER JOIN Example
SELECT Customers.CustomerName, Orders.Product
FROM Customers
INNER JOIN Orders
ON Customers.CustomerID = Orders.CustomerID;
🔍 Output:
CustomerName	Product
Alice	Laptop
Charlie	Phone
💡 Explanation:
    • It joins both tables on CustomerID.
    • Only matching CustomerIDs (1 and 3) are present in both tables.
    • Customer with ID 4 (in Orders) is ignored because there's no match in Customers.

🛠️ Use Case Scenarios
    • Joining employees with their departments
    • Linking students with their courses
    • Fetching orders along with customer information

🔄 INNER JOIN with Aliases
You can also use aliases to make your query cleaner:
SELECT c.CustomerName, o.Product
FROM Customers c
INNER JOIN Orders o
ON c.CustomerID = o.CustomerID;

🧪 Multiple INNER JOINs
If you need to join more than two tables:
SELECT e.Name, d.DepartmentName, p.ProjectName
FROM Employees e
INNER JOIN Departments d ON e.DepartmentID = d.DepartmentID
INNER JOIN Projects p ON e.ProjectID = p.ProjectID;

📝 Notes
    • INNER JOIN is the default type of JOIN. You can even write JOIN instead of INNER JOIN.
    • If you're ever seeing fewer rows than expected in your join, make sure both sides of the join condition have matching values.

🔍 What is a LEFT JOIN?
A LEFT JOIN (also called LEFT OUTER JOIN) returns:
    • ✅ All records from the left table
    • ➕ Matched records from the right table
    • ❌ If there is no match, the result from the right table will be NULL

🧠 Syntax
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column_name = table2.column_name;
Here, table1 is the left table, and table2 is the right table.

📘 Example Tables
🧾 Customers
CustomerID	CustomerName
1	Alice
2	Bob
3	Charlie
4	David
📦 Orders
OrderID	CustomerID	Product
101	1	Laptop
102	3	Phone

✅ LEFT JOIN Example
SELECT Customers.CustomerName, Orders.Product
FROM Customers
LEFT JOIN Orders
ON Customers.CustomerID = Orders.CustomerID;
🔍 Output:
CustomerName	Product
Alice	Laptop
Bob	NULL
Charlie	Phone
David	NULL

💡 Explanation:
    • Alice and Charlie have matching orders.
    • Bob and David don’t have any orders → so Product is NULL for them.
    • This is the key difference between INNER JOIN and LEFT JOIN:
        ○ INNER JOIN: only matched records
        ○ LEFT JOIN: all left table records, matched or not

🧪 LEFT JOIN with SELECT *
SELECT *
FROM Customers
LEFT JOIN Orders
ON Customers.CustomerID = Orders.CustomerID;
Returns all columns from both tables (with NULLs for non-matching right-side rows).

📊 Visualization
Customers (LEFT)
+--------------+
| CustomerID   |
| CustomerName |
+--------------+
Orders (RIGHT)
+------------+
| CustomerID |
| Product    |
+------------+
LEFT JOIN Result
+--------------+---------+
| CustomerName | Product |
+--------------+---------+
| Alice        | Laptop  |
| Bob          | NULL    |
| Charlie      | Phone   |
| David        | NULL    |

🔎 Real-world Use Case
    • Show all customers, even if they haven’t placed an order yet.
    • Show all employees, even if they’re not assigned to any project.

✍️ Summary
JOIN Type	Returns
INNER JOIN	Only matched records
LEFT JOIN	All from left + matched from right


🔍 What is a RIGHT JOIN?
A RIGHT JOIN (or RIGHT OUTER JOIN) returns:
    • ✅ All records from the right table
    • ➕ Matched records from the left table
    • ❌ If there is no match, values from the left table will be NULL

🧠 Syntax
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column_name = table2.column_name;
    table2 is considered the right table, and its rows will always be included, whether or not a match exists in table1.

📘 Example Tables
🧾 Customers (left table)
CustomerID	CustomerName
1	Alice
2	Bob
3	Charlie
📦 Orders (right table)
OrderID	CustomerID	Product
101	1	Laptop
102	3	Phone
103	4	Tablet

✅ RIGHT JOIN Example
SELECT Customers.CustomerName, Orders.Product
FROM Customers
RIGHT JOIN Orders
ON Customers.CustomerID = Orders.CustomerID;
🔍 Output:
CustomerName	Product
Alice	Laptop
Charlie	Phone
NULL	Tablet

💡 Explanation:
    • Alice and Charlie placed orders → matched ✅
    • Order with CustomerID = 4 has no match in Customers → so CustomerName = NULL
    • All Orders are shown (right table), even unmatched ones.

🔁 RIGHT JOIN vs LEFT JOIN
JOIN Type	Includes all rows from...
LEFT JOIN	Left table
RIGHT JOIN	Right table
You could say:
-- LEFT JOIN
FROM A
LEFT JOIN B ON A.id = B.id
-- RIGHT JOIN (same as above flipped)
FROM B
RIGHT JOIN A ON B.id = A.id
They’re functionally reversible — just depends on which table is "left" or "right."

🔹 SELECT * with RIGHT JOIN
SELECT *
FROM Customers
RIGHT JOIN Orders
ON Customers.CustomerID = Orders.CustomerID;
This will return all columns from both tables, with NULLs in the Customers fields where there's no match.

🧪 Real-World Use Case
    • Show all orders, even if some don’t have valid customer info (e.g., missing foreign keys).
    • Audit records where orders exist but the customer data was deleted.


🔍 What is a FULL JOIN?
A FULL JOIN (or FULL OUTER JOIN) returns:
    ✅ All records from the left table
    ✅ All records from the right table
    🔁 Matched records are shown together
    ❌ Unmatched records from either side are filled with NULL on the other side

🧠 Syntax
SELECT columns
FROM table1
FULL JOIN table2
ON table1.column_name = table2.column_name;

📘 Example Tables
🧾 Customers (left table)
CustomerID	CustomerName
1	Alice
2	Bob
3	Charlie
📦 Orders (right table)
OrderID	CustomerID	Product
101	1	Laptop
102	3	Phone
103	4	Tablet

✅ FULL JOIN Example
SELECT Customers.CustomerName, Orders.Product
FROM Customers
FULL JOIN Orders
ON Customers.CustomerID = Orders.CustomerID;
🔍 Output:
CustomerName	Product
Alice	Laptop
Bob	NULL
Charlie	Phone
NULL	Tablet

💡 Explanation:
    Alice and Charlie have matching orders → ✅
    Bob exists in Customers but has no order → Product = NULL
    OrderID 103 (Tablet) exists in Orders but has no matching customer → CustomerName = NULL
FULL JOIN = LEFT JOIN + RIGHT JOIN

🔹 SELECT * with FULL JOIN
SELECT *
FROM Customers
FULL JOIN Orders
ON Customers.CustomerID = Orders.CustomerID;
Returns all columns from both tables and fills unmatched parts with NULL.

📊 Visual Recap
        FULL JOIN
  ----------------------
 |         |            |
 |   A ∩ B |  A only     |
 |         |            |
 |---------|------------|
 |  B only (right side) |
  ----------------------


🧪 Real-World Use Case
    When you want to combine two data sources and see everything:
        All customers (even without orders)
        All orders (even with missing customer info)
    Reporting or cleanup tasks where missing relationships are important to see

⚠️ Note
Not all databases support FULL JOIN natively (especially older ones or MySQL without workarounds). If needed, you can simulate it using UNION:
SELECT *
FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID
UNION
SELECT *
FROM Customers
RIGHT JOIN Orders ON Customers.CustomerID = Orders.CustomerID


✅ 1. CROSS JOIN
This one is not like the others.
🔍 What is it?
A CROSS JOIN returns the Cartesian product of two tables.
That means: every row from the first table is combined with every row from the second table.
📘 Example:
Table A:
ID	Name
1	Apple
2	Banana
Table B:
ID	Color
1	Red
2	Yellow
SELECT *
FROM TableA
CROSS JOIN TableB;
🔍 Output:
Name	Color
Apple	Red
Apple	Yellow
Banana	Red
Banana	Yellow
📌 If TableA has 3 rows and TableB has 4 → result will have 3 × 4 = 12 rows.
🧠 Use case: To generate combinations — e.g., all possible product-color variations.

✅ 2. SELF JOIN
This isn’t a new join type but a way to use a JOIN on the same table.
🔍 What is it?
A SELF JOIN is when a table joins with itself to compare rows within the same table.
📘 Example:
Imagine a Employees table:
EmpID	Name	ManagerID
1	Alice	NULL
2	Bob	1
3	Carol	1
You want to get the name of each employee and their manager's name.
SELECT E.Name AS Employee, M.Name AS Manager
FROM Employees E
LEFT JOIN Employees M ON E.ManagerID = M.EmpID;
🔍 Output:
Employee	Manager
Alice	NULL
Bob	Alice
Carol	Alice
🧠 Use case: Org charts, hierarchy structures, comparing rows in the same table.

✅ 3. NATURAL JOIN (not commonly used)
This one is found in some databases (like MySQL, PostgreSQL), but not SQL Server.
🔍 What is it?
A NATURAL JOIN automatically joins tables based on columns with the same names and types.
SELECT *
FROM Customers
NATURAL JOIN Orders;
⚠️ Dangerous in big databases: it joins automatically without you explicitly saying which column to join on.

✅ 4. ANTI JOIN (Simulated using NOT EXISTS or LEFT JOIN)
🔍 What is it?
An ANTI JOIN returns rows from the left table that have no match in the right table.
SQL doesn't have a keyword ANTI JOIN, but you can simulate it like this:
-- Using NOT EXISTS
SELECT *
FROM Customers c
WHERE NOT EXISTS (
  SELECT 1
  FROM Orders o
  WHERE o.CustomerID = c.CustomerID
);
or
-- Using LEFT JOIN and WHERE NULL
SELECT c.*
FROM Customers c
LEFT JOIN Orders o ON c.CustomerID = o.CustomerID
WHERE o.CustomerID IS NULL;
🧠 Use case: Find customers who haven’t placed any orders.

✅ 5. SEMI JOIN (Also simulated)
A SEMI JOIN returns rows from the left table where a match exists in the right table — but doesn't return columns from the right table.
Simulated with EXISTS:
SELECT *
FROM Customers c
WHERE EXISTS (
  SELECT 1
  FROM Orders o
  WHERE o.CustomerID = c.CustomerID
);
🧠 Use case: When you just care if a match exists — not what the matched data is.

🔚 Summary of All Joins
Join Type	Description
INNER JOIN	Matching rows from both tables
LEFT JOIN	All from left + matched from right
RIGHT JOIN	All from right + matched from left
FULL JOIN	All rows from both, with NULLs where no match
CROSS JOIN	Cartesian product (all combinations)
SELF JOIN	Table joined to itself
NATURAL JOIN	Auto join on same-named columns (not recommended)
ANTI JOIN	Rows in left table without matches in right
SEMI JOIN	Rows in left table with matches in right (no right-side columns)
