# SQL JOIN and Aggregate Functions Assignment

This README contains 45 SQL questions with answers, explanations, examples, solutions, and outputs.

## Q1. Retrieve EmployeeName, EmployeeID, and DepartmentName for all employees who belong to a department.

### SQL Answer

```sql
SELECT
    e.EmployeeName,
    e.EmployeeID,
    d.DepartmentName
FROM Employees e
INNER JOIN Departments d
    ON e.DepartmentID = d.DepartmentID;
```

### Why We Use This Query

To retrieve employee details together with their department names.

### How This Query Works

- `INNER JOIN` matches employees and departments using `DepartmentID`.
- Only employees having a matching department are displayed.

### Example

Suppose the `Employees` table contains:

| EmployeeID | EmployeeName | DepartmentID |
|---|---|---|
| 1 | Rahul | 10 |
| 2 | Priya | 20 |
| 3 | Amit | NULL |

Suppose the `Departments` table contains:

| DepartmentID | DepartmentName |
|---|---|
| 10 | IT |
| 20 | HR |

### Solution

The `INNER JOIN` matches employees with departments using `DepartmentID`. Employees without a matching department are not displayed.

### Output

| EmployeeName | EmployeeID | DepartmentName |
|---|---|---|
| Rahul | 1 | IT |
| Priya | 2 | HR |

---

## Q2. Find ProductName, CategoryName, and SupplierName for all products.

### SQL Answer

```sql
SELECT
    p.ProductName,
    c.CategoryName,
    s.SupplierName
FROM Products p
INNER JOIN Categories c
    ON p.CategoryID = c.CategoryID
INNER JOIN Suppliers s
    ON p.SupplierID = s.SupplierID;
```

### Why We Use This Query

To display each product along with its category and supplier.

### How This Query Works

- `INNER JOIN` connects Products with Categories and Suppliers through their matching IDs.

### Example

Suppose the `Products` table contains:

| ProductID | ProductName | CategoryID | SupplierID |
|---|---|---|---|
| 1 | Laptop | 10 | 101 |
| 2 | Keyboard | 20 | 102 |
| 3 | Mouse | 10 | 101 |

Suppose the `Categories` table contains:

| CategoryID | CategoryName |
|---|---|
| 10 | Electronics |
| 20 | Accessories |

Suppose the `Suppliers` table contains:

| SupplierID | SupplierName |
|---|---|
| 101 | Tech World |
| 102 | Office Supplies |

### Solution

The query returns products with their matching category and supplier information.

### Output

| ProductName | CategoryName | SupplierName |
|---|---|---|
| Laptop | Electronics | Tech World |
| Keyboard | Accessories | Office Supplies |
| Mouse | Electronics | Tech World |

---

## Q3. Retrieve all orders with customer details CustomerName, Address, and Phone.

### SQL Answer

```sql
SELECT
    o.OrderID,
    o.OrderDate,
    c.CustomerName,
    c.Address,
    c.Phone
FROM Orders o
INNER JOIN Customers c
    ON o.CustomerID = c.CustomerID;
```

### Why We Use This Query

To show order information together with the customer who placed each order.

### How This Query Works

- `INNER JOIN` matches Orders and Customers using `CustomerID`.

### Example

Suppose the `Orders` table contains:

| OrderID | CustomerID | OrderDate |
|---|---|---|
| 101 | 1 | 2022-01-05 |
| 102 | 2 | 2022-01-10 |

Suppose the `Customers` table contains:

| CustomerID | CustomerName | Address | Phone |
|---|---|---|---|
| 1 | Rahul | Vadodara | 9876543210 |
| 2 | Priya | Ahmedabad | 9876501234 |

### Solution

Every order is displayed with the details of its matching customer.

### Output

| OrderID | OrderDate | CustomerName | Address | Phone |
|---|---|---|---|---|
| 101 | 2022-01-05 | Rahul | Vadodara | 9876543210 |
| 102 | 2022-01-10 | Priya | Ahmedabad | 9876501234 |

---

## Q4. Find EmployeeName, Salary, and DepartmentName for employees in the Sales department.

### SQL Answer

```sql
SELECT
    e.EmployeeName,
    e.Salary,
    d.DepartmentName
FROM Employees e
INNER JOIN Departments d
    ON e.DepartmentID = d.DepartmentID
WHERE d.DepartmentName = 'Sales';
```

### Why We Use This Query

To retrieve only employees working in the Sales department.

### How This Query Works

- `INNER JOIN` connects employees to departments, while `WHERE` filters the result to Sales.

### Example

Suppose the `Employees` table contains:

| EmployeeID | EmployeeName | Salary | DepartmentID |
|---|---|---|---|
| 1 | Rahul | 55000 | 10 |
| 2 | Priya | 60000 | 20 |
| 3 | Amit | 50000 | 10 |

Suppose the `Departments` table contains:

| DepartmentID | DepartmentName |
|---|---|
| 10 | Sales |
| 20 | IT |

### Solution

Only employees whose department name is Sales are returned.

### Output

| EmployeeName | Salary | DepartmentName |
|---|---|---|
| Rahul | 55000 | Sales |
| Amit | 50000 | Sales |

---

## Q5. List all products with their suppliers. Display ProductName and SupplierName.

### SQL Answer

```sql
SELECT
    p.ProductName,
    s.SupplierName
FROM Products p
INNER JOIN Suppliers s
    ON p.SupplierID = s.SupplierID;
```

### Why We Use This Query

To identify which supplier provides each product.

### How This Query Works

- `INNER JOIN` matches products and suppliers using `SupplierID`.

### Example

Suppose the `Products` table contains:

| ProductID | ProductName | SupplierID |
|---|---|---|
| 1 | Laptop | 101 |
| 2 | Keyboard | 102 |

Suppose the `Suppliers` table contains:

| SupplierID | SupplierName |
|---|---|
| 101 | Tech World |
| 102 | Office Supplies |

### Solution

Each product is displayed with its matching supplier.

### Output

| ProductName | SupplierName |
|---|---|
| Laptop | Tech World |
| Keyboard | Office Supplies |

---

## Q6. Retrieve all products and their categories. Display NULL if a product is not assigned to any category.

### SQL Answer

```sql
SELECT p.ProductName, c.CategoryName
FROM Products p
LEFT JOIN Categories c ON p.CategoryID = c.CategoryID;
```

### Why We Use This Query

To display every product, even products without a category.

### How This Query Works

- `LEFT JOIN` keeps all rows from Products and displays NULL when no category matches.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query returns the required records while preserving unmatched rows according to the selected join type.

### Output

| ProductName | CategoryName |
|---|---|
| Laptop | Electronics |
| Printer | NULL |

---

## Q7. Find all employees and their managers. Display NULL if an employee has no manager.

### SQL Answer

```sql
SELECT e.EmployeeName AS EmployeeName, m.EmployeeName AS ManagerName
FROM Employees e
LEFT JOIN Employees m ON e.ManagerID = m.EmployeeID;
```

### Why We Use This Query

To display employees and their reporting managers.

### How This Query Works

- This is a self-join.
- The Employees table is used twice: once for employees and once for managers.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query returns the required records while preserving unmatched rows according to the selected join type.

### Output

| EmployeeName | ManagerName |
|---|---|
| Rahul | NULL |
| Priya | Rahul |

---

## Q8. List all customers and their orders. Include customers who have no orders.

### SQL Answer

```sql
SELECT c.CustomerName, o.OrderID, o.OrderDate
FROM Customers c
LEFT JOIN Orders o ON c.CustomerID = o.CustomerID;
```

### Why We Use This Query

To show all customers, including customers who have never placed an order.

### How This Query Works

- `LEFT JOIN` preserves all customers and fills order columns with NULL when no order exists.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query returns the required records while preserving unmatched rows according to the selected join type.

### Output

| CustomerName | OrderID | OrderDate |
|---|---|---|
| Rahul | 101 | 2022-01-05 |
| Amit | NULL | NULL |

---

## Q9. Find all employees and department details. Include employees with no department.

### SQL Answer

```sql
SELECT e.EmployeeName, e.EmployeeID, d.DepartmentName
FROM Employees e
LEFT JOIN Departments d ON e.DepartmentID = d.DepartmentID;
```

### Why We Use This Query

To display every employee, even if department information is missing.

### How This Query Works

- `LEFT JOIN` keeps every employee and returns NULL for unmatched department details.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query returns the required records while preserving unmatched rows according to the selected join type.

### Output

| EmployeeName | EmployeeID | DepartmentName |
|---|---|---|
| Rahul | 1 | IT |
| Amit | 3 | NULL |

---

## Q10. Display all students and their enrolled subjects. Display NULL if a student has no subject.

### SQL Answer

```sql
SELECT s.StudentName, sub.SubjectName
FROM Students s
LEFT JOIN StudentSubjects ss ON s.StudentID = ss.StudentID
LEFT JOIN Subjects sub ON ss.SubjectID = sub.SubjectID;
```

### Why We Use This Query

To show all students and their enrolled subjects.

### How This Query Works

- The first join connects students to enrollment records.
- The second join retrieves subject names.
- Missing subjects appear as NULL.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query returns the required records while preserving unmatched rows according to the selected join type.

### Output

| StudentName | SubjectName |
|---|---|
| Rahul | DBMS |
| Amit | NULL |

---

## Q11. List all products and sales orders. Include all sales orders even if no product is associated.

### SQL Answer

```sql
SELECT p.ProductName, o.OrderID, o.OrderDate
FROM Products p
RIGHT JOIN OrderDetails od ON p.ProductID = od.ProductID
RIGHT JOIN Orders o ON od.OrderID = o.OrderID;
```

### Why We Use This Query

To ensure every sales order is displayed, even if product information is missing.

### How This Query Works

- `RIGHT JOIN` preserves all rows from the right-side table, Orders.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query returns the required records while preserving unmatched rows according to the selected join type.

### Output

| ProductName | OrderID | OrderDate |
|---|---|---|
| Laptop | 101 | 2022-01-05 |
| NULL | 102 | 2022-01-10 |

---

## Q12. List all employees and projects. Include all projects even if no employee is assigned.

### SQL Answer

```sql
SELECT e.EmployeeName, p.ProjectName
FROM Employees e
RIGHT JOIN EmployeeProjects ep ON e.EmployeeID = ep.EmployeeID
RIGHT JOIN Projects p ON ep.ProjectID = p.ProjectID;
```

### Why We Use This Query

To display every project, including projects without assigned employees.

### How This Query Works

- `RIGHT JOIN` preserves all projects and shows NULL for missing employee details.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query returns the required records while preserving unmatched rows according to the selected join type.

### Output

| EmployeeName | ProjectName |
|---|---|
| Rahul | Website |
| NULL | Mobile App |

---

## Q13. Retrieve all customers and orders, including orders with no customer.

### SQL Answer

```sql
SELECT c.CustomerName, o.OrderID, o.OrderDate
FROM Customers c
RIGHT JOIN Orders o ON c.CustomerID = o.CustomerID;
```

### Why We Use This Query

To display every order, even when its customer record is missing.

### How This Query Works

- `RIGHT JOIN` preserves all orders and returns NULL for unmatched customers.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query returns the required records while preserving unmatched rows according to the selected join type.

### Output

| CustomerName | OrderID | OrderDate |
|---|---|---|
| Rahul | 101 | 2022-01-05 |
| NULL | 102 | 2022-01-10 |

---

## Q14. Find all employees and departments. Include all departments with no employees.

### SQL Answer

```sql
SELECT e.EmployeeName, d.DepartmentName
FROM Employees e
RIGHT JOIN Departments d ON e.DepartmentID = d.DepartmentID;
```

### Why We Use This Query

To display every department, including departments without employees.

### How This Query Works

- `RIGHT JOIN` preserves all departments and shows NULL for departments without employees.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query returns the required records while preserving unmatched rows according to the selected join type.

### Output

| EmployeeName | DepartmentName |
|---|---|
| Rahul | IT |
| NULL | Sales |

---

## Q15. Find all sales orders and associated products. If no product exists, show NULL.

### SQL Answer

```sql
SELECT o.OrderID, p.ProductName
FROM Products p
RIGHT JOIN OrderDetails od ON p.ProductID = od.ProductID
RIGHT JOIN Orders o ON od.OrderID = o.OrderID;
```

### Why We Use This Query

To show all sales orders and any related product information.

### How This Query Works

- `RIGHT JOIN` keeps all orders and displays NULL when no product is associated.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query returns the required records while preserving unmatched rows according to the selected join type.

### Output

| OrderID | ProductName |
|---|---|
| 101 | Laptop |
| 102 | NULL |

---

## Q16. List all customers and orders, including unmatched customers and orders.

### SQL Answer

```sql
SELECT c.CustomerName, o.OrderID, o.OrderDate FROM Customers c FULL OUTER JOIN Orders o ON c.CustomerID = o.CustomerID;
```

### Why We Use This Query

To display every customer and every order, including unmatched records.

### How This Query Works

- `FULL OUTER JOIN` returns matching rows and also preserves unmatched rows from both tables.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| CustomerName | OrderID | OrderDate |
|---|---|---|
| Rahul | 101 | 2022-01-05 |
| Priya | NULL | NULL |
| NULL | 102 | 2022-01-10 |

---

## Q17. Retrieve all employees and projects, including unmatched employees and projects.

### SQL Answer

```sql
SELECT e.EmployeeName, p.ProjectName FROM Employees e FULL OUTER JOIN EmployeeProjects ep ON e.EmployeeID = ep.EmployeeID FULL OUTER JOIN Projects p ON ep.ProjectID = p.ProjectID;
```

### Why We Use This Query

To display all employees and all projects, even when no assignment exists.

### How This Query Works

- The full outer join preserves unmatched employees and projects.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| EmployeeName | ProjectName |
|---|---|
| Rahul | Website |
| Priya | NULL |
| NULL | Mobile App |

---

## Q18. List all students and courses, including unmatched students and courses.

### SQL Answer

```sql
SELECT s.StudentName, c.CourseName FROM Students s FULL OUTER JOIN StudentCourses sc ON s.StudentID = sc.StudentID FULL OUTER JOIN Courses c ON sc.CourseID = c.CourseID;
```

### Why We Use This Query

To show all students and courses regardless of enrollment.

### How This Query Works

- The joins preserve students without courses and courses without students.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| StudentName | CourseName |
|---|---|
| Rahul | DBMS |
| Priya | NULL |
| NULL | Java |

---

## Q19. Find all suppliers and products, including unmatched suppliers and products.

### SQL Answer

```sql
SELECT s.SupplierName, p.ProductName FROM Suppliers s FULL OUTER JOIN Products p ON s.SupplierID = p.SupplierID;
```

### Why We Use This Query

To identify suppliers without products and products without suppliers.

### How This Query Works

- `FULL OUTER JOIN` preserves records from both Suppliers and Products.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| SupplierName | ProductName |
|---|---|
| Tech World | Laptop |
| Office Supplies | NULL |
| NULL | Printer |

---

## Q20. List all orders and products, including orders without products and products never ordered.

### SQL Answer

```sql
SELECT o.OrderID, p.ProductName FROM Orders o FULL OUTER JOIN OrderDetails od ON o.OrderID = od.OrderID FULL OUTER JOIN Products p ON od.ProductID = p.ProductID;
```

### Why We Use This Query

To display all orders and products, including unmatched records.

### How This Query Works

- The full outer join preserves orders without products and products that were never ordered.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| OrderID | ProductName |
|---|---|
| 101 | Laptop |
| 102 | NULL |
| NULL | Printer |

---

## Q21. Find employees who work in the same department as John Doe.

### SQL Answer

```sql
SELECT e.EmployeeName, e.DepartmentID FROM Employees e INNER JOIN Employees j ON e.DepartmentID = j.DepartmentID WHERE j.EmployeeName = 'John Doe' AND e.EmployeeName <> 'John Doe';
```

### Why We Use This Query

To find coworkers who belong to the same department as John Doe.

### How This Query Works

- The Employees table is joined to itself.
- The WHERE clause selects John Doe's department and excludes John Doe.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| EmployeeName | DepartmentID |
|---|---|
| Rahul | 10 |

---

## Q22. List all employees and their managers using a self-join.

### SQL Answer

```sql
SELECT e.EmployeeName AS EmployeeName, m.EmployeeName AS ManagerName FROM Employees e LEFT JOIN Employees m ON e.ManagerID = m.EmployeeID;
```

### Why We Use This Query

To display the reporting relationship between employees and managers.

### How This Query Works

- The same table is used twice with different aliases.
- A left join also includes employees without managers.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| EmployeeName | ManagerName |
|---|---|
| Rahul | NULL |
| Priya | Rahul |

---

## Q23. Find employees with the same department and job title.

### SQL Answer

```sql
SELECT e1.EmployeeName AS Employee1, e2.EmployeeName AS Employee2, e1.DepartmentID, e1.JobTitle FROM Employees e1 INNER JOIN Employees e2 ON e1.DepartmentID = e2.DepartmentID AND e1.JobTitle = e2.JobTitle AND e1.EmployeeID < e2.EmployeeID;
```

### Why We Use This Query

To identify employees who share both department and job title.

### How This Query Works

- The self-join compares employees with the same DepartmentID and JobTitle.
- The ID condition avoids duplicate pairs.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| Employee1 | Employee2 | DepartmentID | JobTitle |
|---|---|---|---|
| Rahul | Priya | 10 | Developer |

---

## Q24. Find employees reporting directly to the same manager.

### SQL Answer

```sql
SELECT e1.EmployeeName AS Employee1, e2.EmployeeName AS Employee2, e1.ManagerID FROM Employees e1 INNER JOIN Employees e2 ON e1.ManagerID = e2.ManagerID AND e1.EmployeeID < e2.EmployeeID WHERE e1.ManagerID IS NOT NULL;
```

### Why We Use This Query

To find employees who report to the same manager.

### How This Query Works

- The self-join matches employees with equal ManagerID values and avoids duplicate pairs.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| Employee1 | Employee2 | ManagerID |
|---|---|---|
| Priya | Amit | 1 |

---

## Q25. Find products with the same category and supplier.

### SQL Answer

```sql
SELECT p1.ProductName AS Product1, p2.ProductName AS Product2, p1.CategoryID, p1.SupplierID FROM Products p1 INNER JOIN Products p2 ON p1.CategoryID = p2.CategoryID AND p1.SupplierID = p2.SupplierID AND p1.ProductID < p2.ProductID;
```

### Why We Use This Query

To find products sharing the same category and supplier.

### How This Query Works

- The Products table is joined to itself using CategoryID and SupplierID.
- The ID condition prevents duplicate pairs.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| Product1 | Product2 | CategoryID | SupplierID |
|---|---|---|---|
| Laptop | Mouse | 10 | 101 |

---

## Q26. List orders placed after January 1, 2022, along with customer details.

### SQL Answer

```sql
SELECT o.OrderID, o.OrderDate, c.CustomerName FROM Orders o INNER JOIN Customers c ON o.CustomerID = c.CustomerID WHERE o.OrderDate > '2022-01-01';
```

### Why We Use This Query

To retrieve recent orders with customer information.

### How This Query Works

- The join connects orders to customers, and WHERE filters dates after January 1, 2022.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| OrderID | OrderDate | CustomerName |
|---|---|---|
| 102 | 2022-01-10 | Priya |

---

## Q27. Find employees with a salary greater than 50,000 in the Sales department.

### SQL Answer

```sql
SELECT e.EmployeeName, e.Salary, d.DepartmentName FROM Employees e INNER JOIN Departments d ON e.DepartmentID = d.DepartmentID WHERE e.Salary > 50000 AND d.DepartmentName = 'Sales';
```

### Why We Use This Query

To find highly paid employees in Sales.

### How This Query Works

- The query joins employees with departments and applies salary and department filters.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| EmployeeName | Salary | DepartmentName |
|---|---:|---|
| Rahul | 60000 | Sales |

---

## Q28. List customers with orders worth more than 200.

### SQL Answer

```sql
SELECT DISTINCT c.CustomerName, o.OrderID FROM Customers c INNER JOIN Orders o ON c.CustomerID = o.CustomerID INNER JOIN OrderDetails od ON o.OrderID = od.OrderID WHERE od.Quantity * od.UnitPrice > 200;
```

### Why We Use This Query

To identify customers who placed orders worth more than 200.

### How This Query Works

- The query joins customers, orders, and order details, then calculates order value using Quantity multiplied by UnitPrice.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| CustomerName | OrderID |
|---|---|
| Rahul | 101 |

---

## Q29. Find IT employees with a salary greater than 60,000.

### SQL Answer

```sql
SELECT e.EmployeeName, e.Salary, d.DepartmentName FROM Employees e INNER JOIN Departments d ON e.DepartmentID = d.DepartmentID WHERE d.DepartmentName = 'IT' AND e.Salary > 60000;
```

### Why We Use This Query

To find employees in IT whose salary exceeds 60,000.

### How This Query Works

- The WHERE clause filters by department and salary after joining both tables.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| EmployeeName | Salary | DepartmentName |
|---|---:|---|
| Rahul | 65000 | IT |

---

## Q30. Retrieve the name and address of employees assigned to project P123.

### SQL Answer

```sql
SELECT e.EmployeeName, e.Address, p.ProjectName FROM Employees e INNER JOIN EmployeeProjects ep ON e.EmployeeID = ep.EmployeeID INNER JOIN Projects p ON ep.ProjectID = p.ProjectID WHERE p.ProjectID = 'P123';
```

### Why We Use This Query

To find employees assigned to a particular project.

### How This Query Works

- The query joins employees, assignment records, and projects, then filters for project P123.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| EmployeeName | Address | ProjectName |
|---|---|---|
| Rahul | Vadodara | Website Development |

---

## Q31. Find the total number of orders for each customer.

### SQL Answer

```sql
SELECT c.CustomerName, COUNT(o.OrderID) AS TotalOrders FROM Customers c LEFT JOIN Orders o ON c.CustomerID = o.CustomerID GROUP BY c.CustomerName;
```

### Why We Use This Query

To count how many orders each customer has placed.

### How This Query Works

- `COUNT` counts orders and `GROUP BY` creates one result group per customer.
- LEFT JOIN includes customers with zero orders.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| CustomerName | TotalOrders |
|---|---:|
| Rahul | 2 |
| Priya | 1 |
| Amit | 0 |

---

## Q32. Find the average salary for each department.

### SQL Answer

```sql
SELECT d.DepartmentName, AVG(e.Salary) AS AverageSalary FROM Departments d INNER JOIN Employees e ON d.DepartmentID = e.DepartmentID GROUP BY d.DepartmentName;
```

### Why We Use This Query

To calculate the average employee salary by department.

### How This Query Works

- `AVG` calculates the mean salary and `GROUP BY` groups employees by department.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| DepartmentName | AverageSalary |
|---|---:|
| Sales | 55000 |
| IT | 75000 |

---

## Q33. Find the total sales for each product.

### SQL Answer

```sql
SELECT p.ProductName, SUM(od.Quantity * od.UnitPrice) AS TotalSales FROM Products p INNER JOIN OrderDetails od ON p.ProductID = od.ProductID GROUP BY p.ProductName;
```

### Why We Use This Query

To calculate total sales generated by each product.

### How This Query Works

- The query calculates each line value and uses SUM to add values for each product.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| ProductName | TotalSales |
|---|---:|
| Laptop | 1000 |
| Mouse | 300 |

---

## Q34. Find the total number of employees in each department.

### SQL Answer

```sql
SELECT d.DepartmentName, COUNT(e.EmployeeID) AS TotalEmployees FROM Departments d LEFT JOIN Employees e ON d.DepartmentID = e.DepartmentID GROUP BY d.DepartmentName;
```

### Why We Use This Query

To count employees in every department, including empty departments.

### How This Query Works

- LEFT JOIN preserves departments without employees, and COUNT counts matching employee IDs.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| DepartmentName | TotalEmployees |
|---|---:|
| Sales | 3 |
| IT | 2 |
| HR | 0 |

---

## Q35. Find the average order amount for each customer.

### SQL Answer

```sql
SELECT c.CustomerName, AVG(od.Quantity * od.UnitPrice) AS AverageOrderAmount FROM Customers c INNER JOIN Orders o ON c.CustomerID = o.CustomerID INNER JOIN OrderDetails od ON o.OrderID = od.OrderID GROUP BY c.CustomerName;
```

### Why We Use This Query

To calculate the average value of orders placed by each customer.

### How This Query Works

- The query calculates order amounts and uses AVG for each customer group.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| CustomerName | AverageOrderAmount |
|---|---:|
| Rahul | 200 |

---

## Q36. Find the highest-priced product in each category.

### SQL Answer

```sql
SELECT c.CategoryName, MAX(p.Price) AS HighestPrice FROM Categories c INNER JOIN Products p ON c.CategoryID = p.CategoryID GROUP BY c.CategoryName;
```

### Why We Use This Query

To identify the highest product price in each category.

### How This Query Works

- `MAX` returns the largest price in each category group.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| CategoryName | HighestPrice |
|---|---:|
| Electronics | 800 |
| Accessories | 200 |

---

## Q37. Find the total sales revenue for each product.

### SQL Answer

```sql
SELECT p.ProductName, SUM(od.Quantity * od.UnitPrice) AS TotalRevenue FROM Products p INNER JOIN OrderDetails od ON p.ProductID = od.ProductID GROUP BY p.ProductName;
```

### Why We Use This Query

To calculate total revenue generated by every product.

### How This Query Works

- Quantity is multiplied by UnitPrice for each sale, and SUM adds the values by product.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| ProductName | TotalRevenue |
|---|---:|
| Laptop | 1000 |
| Keyboard | 300 |

---

## Q38. Find the minimum, maximum, and average product price for each category.

### SQL Answer

```sql
SELECT c.CategoryName, MIN(p.Price) AS MinimumPrice, MAX(p.Price) AS MaximumPrice, AVG(p.Price) AS AveragePrice FROM Categories c INNER JOIN Products p ON c.CategoryID = p.CategoryID GROUP BY c.CategoryName;
```

### Why We Use This Query

To summarize product prices within each category.

### How This Query Works

- `MIN`, `MAX`, and `AVG` calculate the lowest, highest, and average prices for each group.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| CategoryName | MinimumPrice | MaximumPrice | AveragePrice |
|---|---:|---:|---:|
| Electronics | 500 | 800 | 666.67 |

---

## Q39. Find the total number of employees in each department using COUNT.

### SQL Answer

```sql
SELECT d.DepartmentName, COUNT(e.EmployeeID) AS TotalEmployees FROM Departments d LEFT JOIN Employees e ON d.DepartmentID = e.DepartmentID GROUP BY d.DepartmentName;
```

### Why We Use This Query

To count employees department-wise using COUNT.

### How This Query Works

- COUNT counts employee IDs, while LEFT JOIN includes departments with no employees.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| DepartmentName | TotalEmployees |
|---|---:|
| Sales | 3 |
| IT | 2 |

---

## Q40. Find the total money spent on each order.

### SQL Answer

```sql
SELECT o.OrderID, SUM(od.Quantity * od.UnitPrice) AS TotalOrderAmount FROM Orders o INNER JOIN OrderDetails od ON o.OrderID = od.OrderID GROUP BY o.OrderID;
```

### Why We Use This Query

To calculate the total amount of every order.

### How This Query Works

- The query multiplies quantity by unit price and adds all order-detail amounts using SUM.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| OrderID | TotalOrderAmount |
|---|---:|
| 101 | 1100 |

---

## Q41. Display all students and subjects. Show NULL if a student is not enrolled in any subject.

### SQL Answer

```sql
SELECT s.StudentName, sub.SubjectName FROM Students s LEFT JOIN StudentSubjects ss ON s.StudentID = ss.StudentID LEFT JOIN Subjects sub ON ss.SubjectID = sub.SubjectID;
```

### Why We Use This Query

To display every student and their subjects, including students without enrollment.

### How This Query Works

- LEFT JOIN preserves all students and shows NULL for missing subjects.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| StudentName | SubjectName |
|---|---|
| Rahul | DBMS |
| Amit | NULL |

---

## Q42. Display all employees and their salaries, including NULL salary values.

### SQL Answer

```sql
SELECT e.EmployeeName, s.SalaryAmount FROM Employees e LEFT JOIN Salary s ON e.EmployeeID = s.EmployeeID;
```

### Why We Use This Query

To display every employee even if salary information is unavailable.

### How This Query Works

- LEFT JOIN preserves employees and returns NULL when no salary record matches.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| EmployeeName | SalaryAmount |
|---|---:|
| Rahul | 50000 |
| Amit | NULL |

---

## Q43. Display all orders and their status. Show NULL if no status is assigned.

### SQL Answer

```sql
SELECT o.OrderID, s.StatusName FROM Orders o LEFT JOIN OrderStatus s ON o.StatusID = s.StatusID;
```

### Why We Use This Query

To display every order and its current status.

### How This Query Works

- LEFT JOIN keeps all orders and shows NULL when an order has no matching status.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| OrderID | StatusName |
|---|---|
| 101 | Pending |
| 103 | NULL |

---

## Q44. Display all customers and their phone numbers. Show NULL if a phone number is unavailable.

### SQL Answer

```sql
SELECT c.CustomerName, c.Phone FROM Customers c;
```

### Why We Use This Query

To display every customer and their available phone number.

### How This Query Works

- The query selects all customers.
- Existing NULL phone values remain NULL.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| CustomerName | Phone |
|---|---|
| Rahul | 9876543210 |
| Priya | NULL |

---

## Q45. Display all products and discount information. Show NULL if no discount is assigned.

### SQL Answer

```sql
SELECT p.ProductName, d.DiscountPercentage FROM Products p LEFT JOIN Discounts d ON p.ProductID = d.ProductID;
```

### Why We Use This Query

To display every product and its discount information.

### How This Query Works

- LEFT JOIN preserves all products and shows NULL when no discount record exists.

### Example

Suppose the related tables contain matching sample records.

### Solution

The query applies the required join, filter, grouping, aggregate function, or NULL-handling rule.

### Output

| ProductName | DiscountPercentage |
|---|---:|
| Laptop | 10 |
| Keyboard | NULL |

---

