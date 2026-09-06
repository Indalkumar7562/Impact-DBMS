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

### Example

Suppose the `Employees` table contains:

| EmployeeID | EmployeeName | DepartmentID |
|---|---|---|
| 1 | Rahul | 10 |
| 2 | Priya | 20 |
| 3 | Amit | NULL |

And the `Departments` table contains:

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

### Example

Suppose the `Products` table contains:

| ProductID | ProductName | CategoryID | SupplierID |
|---|---|---|---|
| 1 | Laptop | 10 | 101 |
| 2 | Keyboard | 20 | 102 |
| 3 | Mouse | 10 | 101 |

And the `Categories` table contains:

| CategoryID | CategoryName |
|---|---|
| 10 | Electronics |
| 20 | Accessories |

And the `Suppliers` table contains:

| SupplierID | SupplierName |
|---|---|
| 101 | Tech World |
| 102 | Office Supplies |

### Solution

The `INNER JOIN` combines the `Products`, `Categories`, and `Suppliers` tables using their matching IDs. Only products having a matching category and supplier are displayed.

### Output

| ProductName | CategoryName | SupplierName |
|---|---|---|
| Laptop | Electronics | Tech World |
| Keyboard | Accessories | Office Supplies |
| Mouse | Electronics | Tech World |


## Q3. Retrieve all orders with customer details CustomerName, Address, and Phone. Join Orders and Customers.

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

### Example

Suppose the `Orders` table contains:

| OrderID | CustomerID | OrderDate |
|---|---|---|
| 101 | 1 | 2022-01-05 |
| 102 | 2 | 2022-01-10 |
| 103 | 3 | 2022-01-15 |

And the `Customers` table contains:

| CustomerID | CustomerName | Address | Phone |
|---|---|---|---|
| 1 | Rahul | Vadodara | 9876543210 |
| 2 | Priya | Ahmedabad | 9876501234 |
| 3 | Amit | Surat | 9876512345 |

### Solution

The `INNER JOIN` combines the `Orders` and `Customers` tables using the matching `CustomerID`. Each order is displayed along with the details of the customer who placed it.

### Output

| OrderID | OrderDate | CustomerName | Address | Phone |
|---|---|---|---|---|
| 101 | 2022-01-05 | Rahul | Vadodara | 9876543210 |
| 102 | 2022-01-10 | Priya | Ahmedabad | 9876501234 |
| 103 | 2022-01-15 | Amit | Surat | 9876512345 |

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

### Example

Suppose the `Employees` table contains:

| EmployeeID | EmployeeName | Salary | DepartmentID |
|---|---|---:|---|
| 1 | Rahul | 55000 | 10 |
| 2 | Priya | 60000 | 20 |
| 3 | Amit | 50000 | 10 |

And the `Departments` table contains:

| DepartmentID | DepartmentName |
|---|---|
| 10 | Sales |
| 20 | IT |

### Solution

The `INNER JOIN` combines employees with their departments. The `WHERE` condition displays only employees working in the Sales department.

### Output

| EmployeeName | Salary | DepartmentName |
|---|---:|---|
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

### Example

Suppose the `Products` table contains:

| ProductID | ProductName | SupplierID |
|---|---|---|
| 1 | Laptop | 101 |
| 2 | Keyboard | 102 |
| 3 | Mouse | 101 |

And the `Suppliers` table contains:

| SupplierID | SupplierName |
|---|---|
| 101 | Tech World |
| 102 | Office Supplies |

### Solution

The `INNER JOIN` matches each product with its supplier using `SupplierID`.

### Output

| ProductName | SupplierName |
|---|---|
| Laptop | Tech World |
| Keyboard | Office Supplies |
| Mouse | Tech World |

---

## Q6. Retrieve all products and their categories. Display NULL if a product is not assigned to any category.

### SQL Answer

```sql
SELECT
    p.ProductName,
    c.CategoryName
FROM Products p
LEFT JOIN Categories c
    ON p.CategoryID = c.CategoryID;
```

### Example

Suppose the `Products` table contains:

| ProductID | ProductName | CategoryID |
|---|---|---|
| 1 | Laptop | 10 |
| 2 | Keyboard | 20 |
| 3 | Printer | NULL |

And the `Categories` table contains:

| CategoryID | CategoryName |
|---|---|
| 10 | Electronics |
| 20 | Accessories |

### Solution

The `LEFT JOIN` displays all products. If a product does not have a matching category, the category name is shown as `NULL`.

### Output

| ProductName | CategoryName |
|---|---|
| Laptop | Electronics |
| Keyboard | Accessories |
| Printer | NULL |

---

## Q7. Find all employees and their managers. Display NULL if an employee has no manager.

### SQL Answer

```sql
SELECT
    e.EmployeeName AS EmployeeName,
    m.EmployeeName AS ManagerName
FROM Employees e
LEFT JOIN Employees m
    ON e.ManagerID = m.EmployeeID;
```

### Example

Suppose the `Employees` table contains:

| EmployeeID | EmployeeName | ManagerID |
|---|---|---|
| 1 | Rahul | NULL |
| 2 | Priya | 1 |
| 3 | Amit | 1 |

### Solution

The `SELF JOIN` joins the `Employees` table with itself. The `LEFT JOIN` ensures that employees without managers are also displayed.

### Output

| EmployeeName | ManagerName |
|---|---|
| Rahul | NULL |
| Priya | Rahul |
| Amit | Rahul |

---

## Q8. List all customers and their orders. Include customers who have no orders.

### SQL Answer

```sql
SELECT
    c.CustomerName,
    o.OrderID,
    o.OrderDate
FROM Customers c
LEFT JOIN Orders o
    ON c.CustomerID = o.CustomerID;
```

### Example

Suppose the `Customers` table contains:

| CustomerID | CustomerName |
|---|---|
| 1 | Rahul |
| 2 | Priya |
| 3 | Amit |

And the `Orders` table contains:

| OrderID | CustomerID | OrderDate |
|---|---|---|
| 101 | 1 | 2022-01-05 |
| 102 | 2 | 2022-01-10 |

### Solution

The `LEFT JOIN` displays every customer, including customers who have not placed any order.

### Output

| CustomerName | OrderID | OrderDate |
|---|---|---|
| Rahul | 101 | 2022-01-05 |
| Priya | 102 | 2022-01-10 |
| Amit | NULL | NULL |

---

## Q9. Find all employees and department details. Include employees with no department.

### SQL Answer

```sql
SELECT
    e.EmployeeName,
    e.EmployeeID,
    d.DepartmentName
FROM Employees e
LEFT JOIN Departments d
    ON e.DepartmentID = d.DepartmentID;
```

### Example

Suppose the `Employees` table contains:

| EmployeeID | EmployeeName | DepartmentID |
|---|---|---|
| 1 | Rahul | 10 |
| 2 | Priya | 20 |
| 3 | Amit | NULL |

And the `Departments` table contains:

| DepartmentID | DepartmentName |
|---|---|
| 10 | IT |
| 20 | HR |

### Solution

The `LEFT JOIN` displays all employees. Employees without a department have `NULL` in the department column.

### Output

| EmployeeName | EmployeeID | DepartmentName |
|---|---|---|
| Rahul | 1 | IT |
| Priya | 2 | HR |
| Amit | 3 | NULL |

---

## Q10. Display all students and their enrolled subjects. Display NULL if a student has no subject.

### SQL Answer

```sql
SELECT
    s.StudentName,
    sub.SubjectName
FROM Students s
LEFT JOIN StudentSubjects ss
    ON s.StudentID = ss.StudentID
LEFT JOIN Subjects sub
    ON ss.SubjectID = sub.SubjectID;
```

### Example

Suppose the `Students` table contains:

| StudentID | StudentName |
|---|---|
| 1 | Rahul |
| 2 | Priya |
| 3 | Amit |

And the `StudentSubjects` table contains:

| StudentID | SubjectID |
|---|---|
| 1 | 101 |
| 2 | 102 |

And the `Subjects` table contains:

| SubjectID | SubjectName |
|---|---|
| 101 | DBMS |
| 102 | Java |

### Solution

The `LEFT JOIN` displays all students. Students without enrolled subjects are shown with `NULL`.

### Output

| StudentName | SubjectName |
|---|---|
| Rahul | DBMS |
| Priya | Java |
| Amit | NULL |

---

## Q11. List all products and sales orders. Include all sales orders even if no product is associated.

### SQL Answer

```sql
SELECT
    p.ProductName,
    o.OrderID,
    o.OrderDate
FROM Products p
RIGHT JOIN OrderDetails od
    ON p.ProductID = od.ProductID
RIGHT JOIN Orders o
    ON od.OrderID = o.OrderID;
```

### Example

Suppose the `Orders` table contains:

| OrderID | OrderDate |
|---|---|
| 101 | 2022-01-05 |
| 102 | 2022-01-10 |

And the `OrderDetails` table contains:

| OrderID | ProductID |
|---|---|
| 101 | 1 |

And the `Products` table contains:

| ProductID | ProductName |
|---|---|
| 1 | Laptop |

### Solution

The `RIGHT JOIN` ensures that all orders are displayed, even when an order does not have an associated product.

### Output

| ProductName | OrderID | OrderDate |
|---|---|---|
| Laptop | 101 | 2022-01-05 |
| NULL | 102 | 2022-01-10 |

---

## Q12. List all employees and projects. Include all projects even if no employee is assigned.

### SQL Answer

```sql
SELECT
    e.EmployeeName,
    p.ProjectName
FROM Employees e
RIGHT JOIN EmployeeProjects ep
    ON e.EmployeeID = ep.EmployeeID
RIGHT JOIN Projects p
    ON ep.ProjectID = p.ProjectID;
```

### Example

Suppose the `Projects` table contains:

| ProjectID | ProjectName |
|---|---|
| 101 | Website |
| 102 | Mobile App |

And the `EmployeeProjects` table contains:

| EmployeeID | ProjectID |
|---|---|
| 1 | 101 |

And the `Employees` table contains:

| EmployeeID | EmployeeName |
|---|---|
| 1 | Rahul |

### Solution

The `RIGHT JOIN` displays all projects, including projects without assigned employees.

### Output

| EmployeeName | ProjectName |
|---|---|
| Rahul | Website |
| NULL | Mobile App |

---

## Q13. Retrieve all customers and orders, including orders with no customer.

### SQL Answer

```sql
SELECT
    c.CustomerName,
    o.OrderID,
    o.OrderDate
FROM Customers c
RIGHT JOIN Orders o
    ON c.CustomerID = o.CustomerID;
```

### Example

Suppose the `Customers` table contains:

| CustomerID | CustomerName |
|---|---|
| 1 | Rahul |
| 2 | Priya |

And the `Orders` table contains:

| OrderID | CustomerID | OrderDate |
|---|---|---|
| 101 | 1 | 2022-01-05 |
| 102 | 3 | 2022-01-10 |

### Solution

The `RIGHT JOIN` displays all orders. If an order has no matching customer, customer details are shown as `NULL`.

### Output

| CustomerName | OrderID | OrderDate |
|---|---|---|
| Rahul | 101 | 2022-01-05 |
| NULL | 102 | 2022-01-10 |

---

## Q14. Find all employees and departments. Include all departments with no employees.

### SQL Answer

```sql
SELECT
    e.EmployeeName,
    d.DepartmentName
FROM Employees e
RIGHT JOIN Departments d
    ON e.DepartmentID = d.DepartmentID;
```

### Example

Suppose the `Employees` table contains:

| EmployeeID | EmployeeName | DepartmentID |
|---|---|---|
| 1 | Rahul | 10 |
| 2 | Priya | 20 |

And the `Departments` table contains:

| DepartmentID | DepartmentName |
|---|---|
| 10 | IT |
| 20 | HR |
| 30 | Sales |

### Solution

The `RIGHT JOIN` displays all departments, including departments that do not have employees.

### Output

| EmployeeName | DepartmentName |
|---|---|
| Rahul | IT |
| Priya | HR |
| NULL | Sales |

---

## Q15. Find all sales orders and associated products. If no product exists, show NULL.

### SQL Answer

```sql
SELECT
    o.OrderID,
    p.ProductName
FROM Products p
RIGHT JOIN OrderDetails od
    ON p.ProductID = od.ProductID
RIGHT JOIN Orders o
    ON od.OrderID = o.OrderID;
```

### Example

Suppose the `Orders` table contains:

| OrderID |
|---|
| 101 |
| 102 |

And the `OrderDetails` table contains:

| OrderID | ProductID |
|---|---|
| 101 | 1 |

And the `Products` table contains:

| ProductID | ProductName |
|---|---|
| 1 | Laptop |

### Solution

The `RIGHT JOIN` displays all sales orders. Orders without matching products display `NULL` for the product name.

### Output

| OrderID | ProductName |
|---|---|
| 101 | Laptop |
| 102 | NULL |

---

## Q16. List all customers and orders, including unmatched customers and orders.

### SQL Answer

```sql
SELECT
    c.CustomerName,
    o.OrderID,
    o.OrderDate
FROM Customers c
FULL OUTER JOIN Orders o
    ON c.CustomerID = o.CustomerID;
```

### Example

Suppose the `Customers` table contains:

| CustomerID | CustomerName |
|---|---|
| 1 | Rahul |
| 2 | Priya |

And the `Orders` table contains:

| OrderID | CustomerID | OrderDate |
|---|---|---|
| 101 | 1 | 2022-01-05 |
| 102 | 3 | 2022-01-10 |

### Solution

The `FULL OUTER JOIN` displays all customers and all orders. Unmatched records contain `NULL` values.

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
SELECT
    e.EmployeeName,
    p.ProjectName
FROM Employees e
FULL OUTER JOIN EmployeeProjects ep
    ON e.EmployeeID = ep.EmployeeID
FULL OUTER JOIN Projects p
    ON ep.ProjectID = p.ProjectID;
```

### Example

Suppose the `Employees` table contains:

| EmployeeID | EmployeeName |
|---|---|
| 1 | Rahul |
| 2 | Priya |

And the `Projects` table contains:

| ProjectID | ProjectName |
|---|---|
| 101 | Website |
| 102 | Mobile App |

And the `EmployeeProjects` table contains:

| EmployeeID | ProjectID |
|---|---|
| 1 | 101 |

### Solution

The `FULL OUTER JOIN` displays employees and projects even when they do not have matching assignment records.

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
SELECT
    s.StudentName,
    c.CourseName
FROM Students s
FULL OUTER JOIN StudentCourses sc
    ON s.StudentID = sc.StudentID
FULL OUTER JOIN Courses c
    ON sc.CourseID = c.CourseID;
```

### Example

Suppose the `Students` table contains:

| StudentID | StudentName |
|---|---|
| 1 | Rahul |
| 2 | Priya |

And the `Courses` table contains:

| CourseID | CourseName |
|---|---|
| 101 | DBMS |
| 102 | Java |

And the `StudentCourses` table contains:

| StudentID | CourseID |
|---|---|
| 1 | 101 |

### Solution

The `FULL OUTER JOIN` displays all students and courses, including those without matching enrollment records.

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
SELECT
    s.SupplierName,
    p.ProductName
FROM Suppliers s
FULL OUTER JOIN Products p
    ON s.SupplierID = p.SupplierID;
```

### Example

Suppose the `Suppliers` table contains:

| SupplierID | SupplierName |
|---|---|
| 101 | Tech World |
| 102 | Office Supplies |

And the `Products` table contains:

| ProductID | ProductName | SupplierID |
|---|---|---|
| 1 | Laptop | 101 |
| 2 | Printer | 103 |

### Solution

The `FULL OUTER JOIN` displays all suppliers and products. Unmatched suppliers or products contain `NULL` values.

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
SELECT
    o.OrderID,
    p.ProductName
FROM Orders o
FULL OUTER JOIN OrderDetails od
    ON o.OrderID = od.OrderID
FULL OUTER JOIN Products p
    ON od.ProductID = p.ProductID;
```

### Example

Suppose the `Orders` table contains:

| OrderID |
|---|
| 101 |
| 102 |

And the `OrderDetails` table contains:

| OrderID | ProductID |
|---|---|
| 101 | 1 |

And the `Products` table contains:

| ProductID | ProductName |
|---|---|
| 1 | Laptop |
| 2 | Printer |

### Solution

The `FULL OUTER JOIN` displays all orders and all products, including orders without products and products that were never ordered.

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
SELECT
    e.EmployeeName,
    e.DepartmentID
FROM Employees e
INNER JOIN Employees j
    ON e.DepartmentID = j.DepartmentID
WHERE j.EmployeeName = 'John Doe'
  AND e.EmployeeName <> 'John Doe';
```

### Example

Suppose the `Employees` table contains:

| EmployeeID | EmployeeName | DepartmentID |
|---|---|---|
| 1 | John Doe | 10 |
| 2 | Rahul | 10 |
| 3 | Priya | 20 |

### Solution

The `SELF JOIN` joins the `Employees` table with itself. The query finds employees whose department is the same as John Doe's department.

### Output

| EmployeeName | DepartmentID |
|---|---|
| Rahul | 10 |

---

## Q22. List all employees and their managers using a self-join.

### SQL Answer

```sql
SELECT
    e.EmployeeName AS EmployeeName,
    m.EmployeeName AS ManagerName
FROM Employees e
LEFT JOIN Employees m
    ON e.ManagerID = m.EmployeeID;
```

### Example

Suppose the `Employees` table contains:

| EmployeeID | EmployeeName | ManagerID |
|---|---|---|
| 1 | Rahul | NULL |
| 2 | Priya | 1 |
| 3 | Amit | 1 |

### Solution

The `SELF JOIN` uses the same `Employees` table twice. One alias represents the employee and the other represents the manager.

### Output

| EmployeeName | ManagerName |
|---|---|
| Rahul | NULL |
| Priya | Rahul |
| Amit | Rahul |

---

## Q23. Find employees with the same department and job title.

### SQL Answer

```sql
SELECT
    e1.EmployeeName AS Employee1,
    e2.EmployeeName AS Employee2,
    e1.DepartmentID,
    e1.JobTitle
FROM Employees e1
INNER JOIN Employees e2
    ON e1.DepartmentID = e2.DepartmentID
   AND e1.JobTitle = e2.JobTitle
   AND e1.EmployeeID < e2.EmployeeID;
```

### Example

Suppose the `Employees` table contains:

| EmployeeID | EmployeeName | DepartmentID | JobTitle |
|---|---|---|---|
| 1 | Rahul | 10 | Developer |
| 2 | Priya | 10 | Developer |
| 3 | Amit | 20 | Tester |

### Solution

The `SELF JOIN` compares employees with other employees. The condition `e1.EmployeeID < e2.EmployeeID` avoids duplicate pairs.

### Output

| Employee1 | Employee2 | DepartmentID | JobTitle |
|---|---|---|---|
| Rahul | Priya | 10 | Developer |

---

## Q24. Find employees reporting directly to the same manager.

### SQL Answer

```sql
SELECT
    e1.EmployeeName AS Employee1,
    e2.EmployeeName AS Employee2,
    e1.ManagerID
FROM Employees e1
INNER JOIN Employees e2
    ON e1.ManagerID = e2.ManagerID
   AND e1.EmployeeID < e2.EmployeeID
WHERE e1.ManagerID IS NOT NULL;
```

### Example

Suppose the `Employees` table contains:

| EmployeeID | EmployeeName | ManagerID |
|---|---|---|
| 1 | Rahul | NULL |
| 2 | Priya | 1 |
| 3 | Amit | 1 |
| 4 | Neha | 2 |

### Solution

The query compares employees who have the same `ManagerID`. It returns pairs of employees reporting to the same manager.

### Output

| Employee1 | Employee2 | ManagerID |
|---|---|---|
| Priya | Amit | 1 |

---

## Q25. Find products with the same category and supplier.

### SQL Answer

```sql
SELECT
    p1.ProductName AS Product1,
    p2.ProductName AS Product2,
    p1.CategoryID,
    p1.SupplierID
FROM Products p1
INNER JOIN Products p2
    ON p1.CategoryID = p2.CategoryID
   AND p1.SupplierID = p2.SupplierID
   AND p1.ProductID < p2.ProductID;
```

### Example

Suppose the `Products` table contains:

| ProductID | ProductName | CategoryID | SupplierID |
|---|---|---|---|
| 1 | Laptop | 10 | 101 |
| 2 | Mouse | 10 | 101 |
| 3 | Printer | 20 | 102 |

### Solution

The `SELF JOIN` compares products with the same category and supplier. The condition `p1.ProductID < p2.ProductID` prevents duplicate results.

### Output

| Product1 | Product2 | CategoryID | SupplierID |
|---|---|---|---|
| Laptop | Mouse | 10 | 101 |

---

## Q26. List orders placed after January 1, 2022, along with customer details.

### SQL Answer

```sql
SELECT
    o.OrderID,
    o.OrderDate,
    c.CustomerName
FROM Orders o
INNER JOIN Customers c
    ON o.CustomerID = c.CustomerID
WHERE o.OrderDate > '2022-01-01';
```

### Example

Suppose the `Orders` table contains:

| OrderID | CustomerID | OrderDate |
|---|---|---|
| 101 | 1 | 2021-12-25 |
| 102 | 2 | 2022-01-10 |
| 103 | 3 | 2022-02-15 |

And the `Customers` table contains:

| CustomerID | CustomerName |
|---|---|
| 1 | Rahul |
| 2 | Priya |
| 3 | Amit |

### Solution

The `INNER JOIN` combines orders with customers. The `WHERE` condition displays only orders placed after January 1, 2022.

### Output

| OrderID | OrderDate | CustomerName |
|---|---|---|
| 102 | 2022-01-10 | Priya |
| 103 | 2022-02-15 | Amit |

---

## Q27. Find employees with a salary greater than 50,000 in the Sales department.

### SQL Answer

```sql
SELECT
    e.EmployeeName,
    e.Salary,
    d.DepartmentName
FROM Employees e
INNER JOIN Departments d
    ON e.DepartmentID = d.DepartmentID
WHERE e.Salary > 50000
  AND d.DepartmentName = 'Sales';
```

### Example

Suppose the `Employees` table contains:

| EmployeeID | EmployeeName | Salary | DepartmentID |
|---|---|---:|---|
| 1 | Rahul | 60000 | 10 |
| 2 | Priya | 45000 | 10 |
| 3 | Amit | 70000 | 20 |

And the `Departments` table contains:

| DepartmentID | DepartmentName |
|---|---|
| 10 | Sales |
| 20 | IT |

### Solution

The query joins employees with departments and filters employees whose salary is greater than 50,000 and whose department is Sales.

### Output

| EmployeeName | Salary | DepartmentName |
|---|---:|---|
| Rahul | 60000 | Sales |

---

## Q28. List customers with orders worth more than 200.

### SQL Answer

```sql
SELECT DISTINCT
    c.CustomerName,
    o.OrderID
FROM Customers c
INNER JOIN Orders o
    ON c.CustomerID = o.CustomerID
INNER JOIN OrderDetails od
    ON o.OrderID = od.OrderID
WHERE od.Quantity * od.UnitPrice > 200;
```

### Example

Suppose the `OrderDetails` table contains:

| OrderID | ProductID | Quantity | UnitPrice |
|---|---|---:|---:|
| 101 | 1 | 2 | 150 |
| 102 | 2 | 1 | 100 |

And the related customer is Rahul for order 101 and Priya for order 102.

### Solution

The query joins customers, orders, and order details. It calculates the order value using `Quantity * UnitPrice` and displays orders worth more than 200.

### Output

| CustomerName | OrderID |
|---|---|
| Rahul | 101 |

---

## Q29. Find IT employees with a salary greater than 60,000.

### SQL Answer

```sql
SELECT
    e.EmployeeName,
    e.Salary,
    d.DepartmentName
FROM Employees e
INNER JOIN Departments d
    ON e.DepartmentID = d.DepartmentID
WHERE d.DepartmentName = 'IT'
  AND e.Salary > 60000;
```

### Example

Suppose the `Employees` table contains:

| EmployeeID | EmployeeName | Salary | DepartmentID |
|---|---|---:|---|
| 1 | Rahul | 65000 | 20 |
| 2 | Priya | 55000 | 20 |
| 3 | Amit | 70000 | 10 |

And the `Departments` table contains:

| DepartmentID | DepartmentName |
|---|---|
| 10 | Sales |
| 20 | IT |

### Solution

The query displays employees belonging to the IT department whose salary is greater than 60,000.

### Output

| EmployeeName | Salary | DepartmentName |
|---|---:|---|
| Rahul | 65000 | IT |

---

## Q30. Retrieve the name and address of employees assigned to project P123.

### SQL Answer

```sql
SELECT
    e.EmployeeName,
    e.Address,
    p.ProjectName
FROM Employees e
INNER JOIN EmployeeProjects ep
    ON e.EmployeeID = ep.EmployeeID
INNER JOIN Projects p
    ON ep.ProjectID = p.ProjectID
WHERE p.ProjectID = 'P123';
```

### Example

Suppose the `Employees` table contains:

| EmployeeID | EmployeeName | Address |
|---|---|---|
| 1 | Rahul | Vadodara |
| 2 | Priya | Ahmedabad |

And the `Projects` table contains:

| ProjectID | ProjectName |
|---|---|
| P123 | Website Development |
| P124 | Mobile Application |

And the `EmployeeProjects` table contains:

| EmployeeID | ProjectID |
|---|---|
| 1 | P123 |
| 2 | P124 |

### Solution

The query joins employees with project assignments and projects. The `WHERE` condition returns only employees assigned to project P123.

### Output

| EmployeeName | Address | ProjectName |
|---|---|---|
| Rahul | Vadodara | Website Development |

---

## Q31. Find the total number of orders for each customer.

### SQL Answer

```sql
SELECT
    c.CustomerName,
    COUNT(o.OrderID) AS TotalOrders
FROM Customers c
LEFT JOIN Orders o
    ON c.CustomerID = o.CustomerID
GROUP BY
    c.CustomerName;
```

### Example

Suppose Rahul has 2 orders, Priya has 1 order, and Amit has no orders.

### Solution

The `LEFT JOIN` includes all customers. The `COUNT()` function counts the number of orders for each customer, and `GROUP BY` groups the results by customer.

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
SELECT
    d.DepartmentName,
    AVG(e.Salary) AS AverageSalary
FROM Departments d
INNER JOIN Employees e
    ON d.DepartmentID = e.DepartmentID
GROUP BY
    d.DepartmentName;
```

### Example

Suppose the Sales department has salaries of 50,000 and 60,000, while the IT department has salaries of 70,000 and 80,000.

### Solution

The `AVG()` function calculates the average salary for each department. The `GROUP BY` clause groups employees according to their departments.

### Output

| DepartmentName | AverageSalary |
|---|---:|
| Sales | 55000 |
| IT | 75000 |

---

## Q33. Find total sales for each product.

### SQL Answer

```sql
SELECT
    p.ProductName,
    SUM(od.Quantity * od.UnitPrice) AS TotalSales
FROM Products p
INNER JOIN OrderDetails od
    ON p.ProductID = od.ProductID
GROUP BY
    p.ProductName;
```

### Example

Suppose Laptop was sold 2 times at 500 each and Mouse was sold 3 times at 100 each.

### Solution

The query calculates sales using `Quantity * UnitPrice`. The `SUM()` function calculates the total sales for each product.

### Output

| ProductName | TotalSales |
|---|---:|
| Laptop | 1000 |
| Mouse | 300 |

---

## Q34. Find the total number of employees in each department.

### SQL Answer

```sql
SELECT
    d.DepartmentName,
    COUNT(e.EmployeeID) AS TotalEmployees
FROM Departments d
LEFT JOIN Employees e
    ON d.DepartmentID = e.DepartmentID
GROUP BY
    d.DepartmentName;
```

### Example

Suppose Sales has 3 employees, IT has 2 employees, and HR has no employees.

### Solution

The `LEFT JOIN` includes departments with no employees. The `COUNT()` function counts employees in each department.

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
SELECT
    c.CustomerName,
    AVG(od.Quantity * od.UnitPrice) AS AverageOrderAmount
FROM Customers c
INNER JOIN Orders o
    ON c.CustomerID = o.CustomerID
INNER JOIN OrderDetails od
    ON o.OrderID = od.OrderID
GROUP BY
    c.CustomerName;
```

### Example

Suppose Rahul placed two orders worth 100 and 300.

### Solution

The query calculates the amount of each order using `Quantity * UnitPrice`. The `AVG()` function calculates the average order amount for each customer.

### Output

| CustomerName | AverageOrderAmount |
|---|---:|
| Rahul | 200 |

---

## Q36. Find the highest-priced product in each category.

### SQL Answer

```sql
SELECT
    c.CategoryName,
    MAX(p.Price) AS HighestPrice
FROM Categories c
INNER JOIN Products p
    ON c.CategoryID = p.CategoryID
GROUP BY
    c.CategoryName;
```

### Example

Suppose Electronics contains products priced at 500 and 800, while Accessories contains products priced at 100 and 200.

### Solution

The `MAX()` function finds the highest product price in each category. The `GROUP BY` clause groups products by category.

### Output

| CategoryName | HighestPrice |
|---|---:|
| Electronics | 800 |
| Accessories | 200 |

---

## Q37. Find the total sales revenue for each product.

### SQL Answer

```sql
SELECT
    p.ProductName,
    SUM(od.Quantity * od.UnitPrice) AS TotalRevenue
FROM Products p
INNER JOIN OrderDetails od
    ON p.ProductID = od.ProductID
GROUP BY
    p.ProductName;
```

### Example

Suppose Laptop was sold 2 times at 500 each and Keyboard was sold 3 times at 100 each.

### Solution

The query multiplies quantity by unit price for every sale. The `SUM()` function calculates the total revenue for each product.

### Output

| ProductName | TotalRevenue |
|---|---:|
| Laptop | 1000 |
| Keyboard | 300 |

---

## Q38. Find the minimum, maximum, and average product price for each category.

### SQL Answer

```sql
SELECT
    c.CategoryName,
    MIN(p.Price) AS MinimumPrice,
    MAX(p.Price) AS MaximumPrice,
    AVG(p.Price) AS AveragePrice
FROM Categories c
INNER JOIN Products p
    ON c.CategoryID = p.CategoryID
GROUP BY
    c.CategoryName;
```

### Example

Suppose Electronics products have prices of 500, 800, and 700.

### Solution

The `MIN()`, `MAX()`, and `AVG()` functions calculate the minimum, maximum, and average prices for each category.

### Output

| CategoryName | MinimumPrice | MaximumPrice | AveragePrice |
|---|---:|---:|---:|
| Electronics | 500 | 800 | 666.67 |

---

## Q39. Find the total number of employees in each department using COUNT.

### SQL Answer

```sql
SELECT
    d.DepartmentName,
    COUNT(e.EmployeeID) AS TotalEmployees
FROM Departments d
LEFT JOIN Employees e
    ON d.DepartmentID = e.DepartmentID
GROUP BY
    d.DepartmentName;
```

### Example

Suppose the Sales department has 3 employees and the IT department has 2 employees.

### Solution

The `COUNT()` function counts employees in each department. The `LEFT JOIN` also displays departments that have no employees.

### Output

| DepartmentName | TotalEmployees |
|---|---:|
| Sales | 3 |
| IT | 2 |

---

## Q40. Find the total money spent on each order.

### SQL Answer

```sql
SELECT
    o.OrderID,
    SUM(od.Quantity * od.UnitPrice) AS TotalOrderAmount
FROM Orders o
INNER JOIN OrderDetails od
    ON o.OrderID = od.OrderID
GROUP BY
    o.OrderID;
```

### Example

Suppose order 101 contains 2 laptops priced at 500 each and 1 mouse priced at 100.

### Solution

The query calculates the total amount of each order by multiplying quantity by unit price and then applying the `SUM()` function.

### Output

| OrderID | TotalOrderAmount |
|---|---:|
| 101 | 1100 |

---

## Q41. Display all students and subjects. Show NULL if a student is not enrolled in any subject.

### SQL Answer

```sql
SELECT
    s.StudentName,
    sub.SubjectName
FROM Students s
LEFT JOIN StudentSubjects ss
    ON s.StudentID = ss.StudentID
LEFT JOIN Subjects sub
    ON ss.SubjectID = sub.SubjectID;
```

### Example

Suppose Rahul is enrolled in DBMS, Priya is enrolled in Java, and Amit is not enrolled in any subject.

### Solution

The `LEFT JOIN` displays all students. If a student is not enrolled in any subject, the subject name is shown as `NULL`.

### Output

| StudentName | SubjectName |
|---|---|
| Rahul | DBMS |
| Priya | Java |
| Amit | NULL |

---

## Q42. Display all employees and their salaries, including NULL salary values.

### SQL Answer

```sql
SELECT
    e.EmployeeName,
    s.SalaryAmount
FROM Employees e
LEFT JOIN Salary s
    ON e.EmployeeID = s.EmployeeID;
```

### Example

Suppose the `Employees` table contains:

| EmployeeID | EmployeeName |
|---|---|
| 1 | Rahul |
| 2 | Priya |
| 3 | Amit |

And the `Salary` table contains:

| EmployeeID | SalaryAmount |
|---|---:|
| 1 | 50000 |
| 2 | 60000 |

### Solution

The `LEFT JOIN` displays all employees. If an employee does not have a salary record, the salary value is shown as `NULL`.

### Output

| EmployeeName | SalaryAmount |
|---|---:|
| Rahul | 50000 |
| Priya | 60000 |
| Amit | NULL |

---

## Q43. Display all orders and their status. Show NULL if no status is assigned.

### SQL Answer

```sql
SELECT
    o.OrderID,
    s.StatusName
FROM Orders o
LEFT JOIN OrderStatus s
    ON o.StatusID = s.StatusID;
```

### Example

Suppose the `Orders` table contains:

| OrderID | StatusID |
|---|---|
| 101 | 1 |
| 102 | 2 |
| 103 | NULL |

And the `OrderStatus` table contains:

| StatusID | StatusName |
|---|---|
| 1 | Pending |
| 2 | Delivered |

### Solution

The `LEFT JOIN` displays all orders. Orders without a matching status display `NULL`.

### Output

| OrderID | StatusName |
|---|---|
| 101 | Pending |
| 102 | Delivered |
| 103 | NULL |

---

## Q44. Display all customers and their phone numbers. Show NULL if a phone number is unavailable.

### SQL Answer

```sql
SELECT
    c.CustomerName,
    c.Phone
FROM Customers c;
```

### Example

Suppose the `Customers` table contains:

| CustomerID | CustomerName | Phone |
|---|---|---|
| 1 | Rahul | 9876543210 |
| 2 | Priya | NULL |
| 3 | Amit | 9876512345 |

### Solution

The query displays all customers and their phone numbers. If a phone number is unavailable, the value is shown as `NULL`.

### Output

| CustomerName | Phone |
|---|---|
| Rahul | 9876543210 |
| Priya | NULL |
| Amit | 9876512345 |

---

## Q45. Display all products and discount information. Show NULL if no discount is assigned.

### SQL Answer

```sql
SELECT
    p.ProductName,
    d.DiscountPercentage
FROM Products p
LEFT JOIN Discounts d
    ON p.ProductID = d.ProductID;
```

### Example

Suppose the `Products` table contains:

| ProductID | ProductName |
|---|---|
| 1 | Laptop |
| 2 | Keyboard |
| 3 | Mouse |

And the `Discounts` table contains:

| ProductID | DiscountPercentage |
|---|---:|
| 1 | 10 |
| 3 | 5 |

### Solution

The `LEFT JOIN` displays all products. Products without a discount record display `NULL` in the discount column.

### Output

| ProductName | DiscountPercentage |
|---|---:|
| Laptop | 10 |
| Keyboard | NULL |
| Mouse | 5 |
