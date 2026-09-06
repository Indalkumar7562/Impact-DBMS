1. INNER JOIN
Q1: Write a query to retrieve the EmployeeName, EmployeeID, and DepartmentName for all employees who belong to a department. Join the Employees table with the Departments table.
Answer
SELECT
    e.EmployeeName,
    e.EmployeeID,
    d.DepartmentName
FROM Employees e
INNER JOIN Departments d
    ON e.DepartmentID = d.DepartmentID;
Example with Solution

Input:

EmployeeID	EmployeeName	DepartmentID
101	John Doe	10
102	Priya Shah	20
104	Amit Kumar	NULL

Departments:

DepartmentID	DepartmentName
10	Sales
20	IT

Solution: John Doe and Priya Shah have matching department IDs. Amit Kumar does not, so he is excluded.

Output:

EmployeeName	EmployeeID	DepartmentName
John Doe	101	Sales
Priya Shah	102	IT

Q2: Write a query to find the ProductName, CategoryName, and SupplierName for all products. Join the Products, Categories, and Suppliers tables.
Answer
SELECT
    p.ProductName,
    c.CategoryName,
    s.SupplierName
FROM Products p
INNER JOIN Categories c
    ON p.CategoryID = c.CategoryID
INNER JOIN Suppliers s
    ON p.SupplierID = s.SupplierID;
Example with Solution

Input:

ProductName	CategoryID	SupplierID
Laptop	1	1
Mouse	1	2
Unknown Product	NULL	NULL

Solution: Only products with matching category and supplier records are included.

Output:

ProductName	CategoryName	SupplierName
Laptop	Electronics	ABC Suppliers
Mouse	Electronics	XYZ Suppliers

Q3: Retrieve a list of all orders, along with their customer details (CustomerName, Address, Phone). Join the Orders and Customers tables.
Answer
SELECT
    o.OrderID,
    c.CustomerName,
    c.Address,
    c.Phone
FROM Orders o
INNER JOIN Customers c
    ON o.CustomerID = c.CustomerID;
Example with Solution

Input:

OrderID	CustomerID
1001	1
1002	2
1004	99

Solution: Orders 1001 and 1002 have matching customers. Order 1004 has no matching customer.

Output:

OrderID	CustomerName	Address	Phone
1001	Rahul	Vadodara	9876543210
1002	Amit	Ahmedabad	NULL

Q4: Write a query to find the EmployeeName, Salary, and DepartmentName for all employees who work in the "Sales" department.
Answer
SELECT
    e.EmployeeName,
    e.Salary,
    d.DepartmentName
FROM Employees e
INNER JOIN Departments d
    ON e.DepartmentID = d.DepartmentID
WHERE d.DepartmentName = 'Sales';
Example with Solution

Input:

EmployeeName	Salary	DepartmentName
John Doe	55000	Sales
Priya Shah	70000	IT
Rahul Patel	60000	Sales

Solution: The WHERE clause selects only employees whose department is Sales.

Output:

EmployeeName	Salary	DepartmentName
John Doe	55000	Sales
Rahul Patel	60000	Sales

Q5: Write a query to list all products with their suppliers. Display ProductName and SupplierName. Join the Products and Suppliers tables.
Answer
SELECT
    p.ProductName,
    s.SupplierName
FROM Products p
INNER JOIN Suppliers s
    ON p.SupplierID = s.SupplierID;
Example with Solution

Input:

ProductName	SupplierID
Laptop	1
Mouse	2
Chair	1
Unknown Product	NULL

Solution: Products with matching suppliers are displayed.

Output:

ProductName	SupplierName
Laptop	ABC Suppliers
Mouse	XYZ Suppliers
Chair	ABC Suppliers
2. LEFT JOIN (LEFT OUTER JOIN)

Q6: Write a query to retrieve all products and their categories. If a product is not assigned to any category, display NULL for the category.
Answer
SELECT
    p.ProductName,
    c.CategoryName
FROM Products p
LEFT JOIN Categories c
    ON p.CategoryID = c.CategoryID;
Example with Solution

Input:

ProductName	CategoryID
Laptop	1
Mouse	1
Chair	2
Unknown Product	NULL

Solution: All products are included. The product without a category gets NULL.

Output:

ProductName	CategoryName
Laptop	Electronics
Mouse	Electronics
Chair	Furniture
Unknown Product	NULL

Q7: Write a query to find all employees and their managers. If an employee doesn't have a manager, show NULL for the manager.
Answer
SELECT
    e.EmployeeName AS Employee,
    m.EmployeeName AS Manager
FROM Employees e
LEFT JOIN Employees m
    ON e.ManagerID = m.EmployeeID;
Example with Solution

Input:

EmployeeID	EmployeeName	ManagerID
101	John Doe	NULL
102	Priya Shah	101
103	Rahul Patel	101
104	Amit Kumar	101

Solution: The same table is joined twice. e represents the employee and m represents the manager.

Output:

Employee	Manager
John Doe	NULL
Priya Shah	John Doe
Rahul Patel	John Doe
Amit Kumar	John Doe

Q8: Write a query to list all customers and the orders they have placed. Show customers who haven't placed any order (i.e., include NULL for orders).
Answer
SELECT
    c.CustomerName,
    o.OrderID,
    o.OrderDate
FROM Customers c
LEFT JOIN Orders o
    ON c.CustomerID = o.CustomerID;
Example with Solution

Input:

CustomerID	CustomerName
1	Rahul
2	Amit
3	Priya

Orders:

OrderID	CustomerID
1001	1
1002	2

Solution: Priya has no order, but she is still included because of LEFT JOIN.

Output:

CustomerName	OrderID	OrderDate
Rahul	1001	2022-02-15
Amit	1002	2022-03-10
Priya	NULL	NULL

Q9: Write a query to find all employees along with their department details. Include employees who don't belong to any department (i.e., show NULL for department).
Answer
SELECT
    e.EmployeeName,
    e.EmployeeID,
    d.DepartmentName
FROM Employees e
LEFT JOIN Departments d
    ON e.DepartmentID = d.DepartmentID;
Example with Solution

Input:

EmployeeID	EmployeeName	DepartmentID
101	John Doe	10
102	Priya Shah	20
104	Amit Kumar	NULL

Solution: Amit Kumar has no department, so his department name is NULL.

Output:

EmployeeName	EmployeeID	DepartmentName
John Doe	101	Sales
Priya Shah	102	IT
Amit Kumar	104	NULL

Q10: Write a query to display all students and the subjects they are enrolled in. If a student is not enrolled in any subject, show NULL for the subject.
Answer
SELECT
    s.StudentName,
    sub.SubjectName
FROM Students s
LEFT JOIN StudentSubjects ss
    ON s.StudentID = ss.StudentID
LEFT JOIN Subjects sub
    ON ss.SubjectID = sub.SubjectID;
Example with Solution

Input:

StudentID	StudentName
1	Rahul
2	Amit
3	Priya

StudentSubjects:

StudentID	SubjectID
1	1
1	2
3	3

Solution: Rahul is enrolled in DBMS and AI. Amit has no enrollment, so NULL is displayed.

Output:

StudentName	SubjectName
Rahul	DBMS
Rahul	AI
Amit	NULL
Priya	Networking
3. RIGHT JOIN (RIGHT OUTER JOIN)

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Q11: Write a query to list all products and the sales orders they belong to. Include all sales orders, even if no product is associated with the order.
Answer
SELECT
    p.ProductName,
    so.SalesOrderID
FROM Products p
RIGHT JOIN SalesOrders so
    ON p.ProductID = so.ProductID;
Example with Solution

Input:

Products

ProductID	ProductName
1	Laptop
2	Mouse

SalesOrders

SalesOrderID	ProductID
5001	1
5002	99

Solution: Sales order 5002 has no matching product, but it is still included because SalesOrders is on the right side.

Output:

ProductName	SalesOrderID
Laptop	5001
NULL	5002

Q12: Write a query to list all employees and the projects they are assigned to. Include all projects, even if no employees are assigned to them.
Answer
SELECT
    e.EmployeeName,
    p.ProjectName
FROM Employees e
RIGHT JOIN EmployeeProjects ep
    ON e.EmployeeID = ep.EmployeeID
RIGHT JOIN Projects p
    ON ep.ProjectID = p.ProjectID;
Example with Solution

Input:

EmployeeProjects

EmployeeID	ProjectID
101	P123
102	P124

Projects

ProjectID	ProjectName
P123	Scholarship Portal
P124	AI Recommendation
P125	Mobile App

Solution: Project P125 has no employee assigned, but it is included.

Output:

EmployeeName	ProjectName
John Doe	Scholarship Portal
Priya Shah	AI Recommendation
NULL	Mobile App

Q13: Write a query to retrieve all customers and their orders, including all orders even if no customer is associated with them.
Answer
SELECT
    c.CustomerName,
    o.OrderID
FROM Customers c
RIGHT JOIN Orders o
    ON c.CustomerID = o.CustomerID;
Example with Solution

Input:

OrderID	CustomerID
1001	1
1002	2
1004	99

Solution: Order 1004 has no matching customer, but it is included.

Output:

CustomerName	OrderID
Rahul	1001
Amit	1002
NULL	1004

Q14: Write a query to find all employees and the departments they belong to. Include all departments even if no employees belong to them.
Answer
SELECT
    e.EmployeeName,
    d.DepartmentName
FROM Employees e
RIGHT JOIN Departments d
    ON e.DepartmentID = d.DepartmentID;
Example with Solution

Input:

Employees

EmployeeName	DepartmentID
John Doe	10
Priya Shah	20

Departments

DepartmentID	DepartmentName
10	Sales
20	IT
30	HR

Solution: HR has no employees, so it is included with NULL.

Output:

EmployeeName	DepartmentName
John Doe	Sales
Priya Shah	IT
NULL	HR

Q15: Write a query to find all sales orders and the products associated with them. If a product is not associated with any order, show the order with NULL for the product.
Answer
SELECT
    so.SalesOrderID,
    p.ProductName
FROM Products p
RIGHT JOIN SalesOrders so
    ON p.ProductID = so.ProductID;
Example with Solution

Input:

SalesOrders

SalesOrderID	ProductID
5001	1
5002	NULL

Products

ProductID	ProductName
1	Laptop
2	Mouse

Solution: Sales order 5002 has no associated product, so ProductName is NULL.

Output:

SalesOrderID	ProductName
5001	Laptop
5002	NULL
4. FULL OUTER JOIN

Important: MySQL does not directly support FULL OUTER JOIN. I’ll show the standard SQL answer and the MySQL equivalent where needed.

Q16: Write a query to list all customers and their orders. Include all customers and all orders, even if a customer hasn't placed any orders or an order is placed by a non-existing customer.
Answer (Standard SQL)
SELECT
    c.CustomerName,
    o.OrderID
FROM Customers c
FULL OUTER JOIN Orders o
    ON c.CustomerID = o.CustomerID;
MySQL Equivalent
SELECT
    c.CustomerName,
    o.OrderID
FROM Customers c
LEFT JOIN Orders o
    ON c.CustomerID = o.CustomerID

UNION

SELECT
    c.CustomerName,
    o.OrderID
FROM Customers c
RIGHT JOIN Orders o
    ON c.CustomerID = o.CustomerID;
Example with Solution

Input:

Customers

CustomerID	CustomerName
1	Rahul
2	Amit
3	Priya

Orders

OrderID	CustomerID
1001	1
1002	2
1004	99

Solution: Rahul and Amit have orders, Priya has no order, and order 1004 has no matching customer.

Output:

CustomerName	OrderID
Rahul	1001
Amit	1002
Priya	NULL
NULL	1004

Q17: Write a query to retrieve all employees and all projects. Include all employees and all projects, even if an employee is not assigned to a project or a project has no employees.
Answer (Standard SQL)
SELECT
    e.EmployeeName,
    p.ProjectName
FROM Employees e
FULL OUTER JOIN EmployeeProjects ep
    ON e.EmployeeID = ep.EmployeeID
FULL OUTER JOIN Projects p
    ON ep.ProjectID = p.ProjectID;
Example with Solution

Input:

Employees

EmployeeID	EmployeeName
101	John Doe
102	Priya Shah
103	Rahul Patel

EmployeeProjects

EmployeeID	ProjectID
101	P123
102	P124

Projects

ProjectID	ProjectName
P123	Scholarship Portal
P124	AI Recommendation
P125	Mobile App

Solution: Rahul is not assigned to a project, and P125 has no employees.

Output:

EmployeeName	ProjectName
John Doe	Scholarship Portal
Priya Shah	AI Recommendation
Rahul Patel	NULL
NULL	Mobile App

Q18: Write a query to list all students and all courses. If a student is not enrolled in any course or a course has no students, show NULL for the course or student.
Answer (Standard SQL)
SELECT
    s.StudentName,
    c.CourseName
FROM Students s
FULL OUTER JOIN StudentCourses sc
    ON s.StudentID = sc.StudentID
FULL OUTER JOIN Courses c
    ON sc.CourseID = c.CourseID;
Example with Solution

Input:

Students

StudentID	StudentName
1	Rahul
2	Amit
3	Priya

StudentCourses

StudentID	CourseID
1	1
3	2

Courses

CourseID	CourseName
1	DBMS
2	AI
3	Cloud Computing

Solution: Amit is not enrolled in any course, and Cloud Computing has no students.

Output:

StudentName	CourseName
Rahul	DBMS
Amit	NULL
Priya	AI
NULL	Cloud Computing

Q19: Write a query to find all suppliers and products. Include all suppliers and all products, even if a supplier has no products or a product has no suppliers.
Answer (Standard SQL)
SELECT
    s.SupplierName,
    p.ProductName
FROM Suppliers s
FULL OUTER JOIN Products p
    ON s.SupplierID = p.SupplierID;
Example with Solution

Input:

Suppliers

SupplierID	SupplierName
1	ABC Suppliers
2	XYZ Suppliers
3	PQR Suppliers

Products

ProductID	ProductName	SupplierID
1	Laptop	1
2	Mouse	2
3	Chair	1
4	Unknown Product	NULL

Solution: PQR Suppliers has no products, and Unknown Product has no supplier.

Output:

SupplierName	ProductName
ABC Suppliers	Laptop
ABC Suppliers	Chair
XYZ Suppliers	Mouse
PQR Suppliers	NULL
NULL	Unknown Product

Q20: Write a query to list all orders and products. Include all orders and products, even if there are orders without products or products not ordered by anyone.
Answer (Standard SQL)
SELECT
    o.OrderID,
    p.ProductName
FROM Orders o
FULL OUTER JOIN OrderDetails od
    ON o.OrderID = od.OrderID
FULL OUTER JOIN Products p
    ON od.ProductID = p.ProductID;
Example with Solution

Input:

Orders

OrderID
1001
1002
1003

OrderDetails

OrderID	ProductID
1001	1
1002	3
1003	2

Products

ProductID	ProductName
1	Laptop
2	Mouse
3	Chair
4	Unknown Product

Solution: Unknown Product has never been ordered, so it appears with NULL for OrderID.

Output:

OrderID	ProductName
1001	Laptop
1002	Chair
1003	Mouse
NULL	Unknown Product
5. SELF JOIN

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Q21: Write a query to find employees who work in the same department as "John Doe". Use the Employees table and join it with itself.
Answer
SELECT
    e.EmployeeName,
    e.DepartmentID
FROM Employees e
INNER JOIN Employees j
    ON e.DepartmentID = j.DepartmentID
WHERE j.EmployeeName = 'John Doe'
  AND e.EmployeeName <> 'John Doe';
Example with Solution

Input:

EmployeeName	DepartmentID
John Doe	10
Priya Shah	20
Rahul Patel	10
Amit Kumar	NULL

Solution: John Doe works in department 10. Rahul Patel also works in department 10, so he is included.

Output:

EmployeeName	DepartmentID
Rahul Patel	10

Q22: Write a query to list all employees and their managers. Use a self-join on the Employees table where the manager is an employee from the same table.
Answer
SELECT
    e.EmployeeName AS Employee,
    m.EmployeeName AS Manager
FROM Employees e
LEFT JOIN Employees m
    ON e.ManagerID = m.EmployeeID;
Example with Solution

Input:

EmployeeID	EmployeeName	ManagerID
101	John Doe	NULL
102	Priya Shah	101
103	Rahul Patel	101

Solution: John Doe has no manager. Priya Shah and Rahul Patel report to John Doe.

Output:

Employee	Manager
John Doe	NULL
Priya Shah	John Doe
Rahul Patel	John Doe

Q23: Write a query to find all employees who share the same department and have the same job title. Use the Employees table with a self-join.
Answer
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
Example with Solution

Input:

EmployeeID	EmployeeName	DepartmentID	JobTitle
101	John Doe	10	Manager
102	Priya Shah	20	Developer
103	Rahul Patel	10	Developer
104	Amit Kumar	10	Developer

Solution: Rahul Patel and Amit Kumar have the same department and job title.

Output:

Employee1	Employee2	DepartmentID	JobTitle
Rahul Patel	Amit Kumar	10	Developer

Q24: Write a query to find all employees who report directly to the same manager. Join the Employees table with itself to find employees under the same manager.
Answer
SELECT
    e1.EmployeeName AS Employee1,
    e2.EmployeeName AS Employee2,
    e1.ManagerID
FROM Employees e1
INNER JOIN Employees e2
    ON e1.ManagerID = e2.ManagerID
   AND e1.EmployeeID < e2.EmployeeID
WHERE e1.ManagerID IS NOT NULL;
Example with Solution

Input:

EmployeeID	EmployeeName	ManagerID
101	John Doe	NULL
102	Priya Shah	101
103	Rahul Patel	101
104	Amit Kumar	101

Solution: Priya Shah, Rahul Patel, and Amit Kumar all report to John Doe.

Output:

Employee1	Employee2	ManagerID
Priya Shah	Rahul Patel	101
Priya Shah	Amit Kumar	101
Rahul Patel	Amit Kumar	101

Q25: Write a query to list all products that belong to the same category and have the same supplier. Join the Products table with itself on CategoryID and SupplierID.
Answer
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
Example with Solution

Input:

ProductID	ProductName	CategoryID	SupplierID
1	Laptop	1	1
2	Mouse	1	2
3	Chair	2	1
4	Keyboard	1	1

Solution: Laptop and Keyboard have the same category and supplier.

Output:

Product1	Product2	CategoryID	SupplierID
Laptop	Keyboard	1	1
6. JOIN with WHERE Clause

Q26: Write a query to list all orders that were placed after January 1st, 2022. Join the Orders and Customers tables and filter by OrderDate.
Answer
SELECT
    o.OrderID,
    c.CustomerName,
    o.OrderDate
FROM Orders o
INNER JOIN Customers c
    ON o.CustomerID = c.CustomerID
WHERE o.OrderDate > '2022-01-01';
Example with Solution

Input:

OrderID	CustomerID	OrderDate
1001	1	2022-02-15
1002	2	2022-03-10
1003	1	2022-04-20

Solution: All three orders were placed after January 1, 2022, and have matching customers.

Output:

OrderID	CustomerName	OrderDate
1001	Rahul	2022-02-15
1002	Amit	2022-03-10
1003	Rahul	2022-04-20

Q27: Write a query to find all employees whose salary is greater than $50,000 and who belong to the "Sales" department. Join the Employees and Departments tables.
Answer
SELECT
    e.EmployeeName,
    e.Salary,
    d.DepartmentName
FROM Employees e
INNER JOIN Departments d
    ON e.DepartmentID = d.DepartmentID
WHERE e.Salary > 50000
  AND d.DepartmentName = 'Sales';
Example with Solution

Input:

EmployeeName	Salary	DepartmentName
John Doe	55000	Sales
Rahul Patel	60000	Sales
Priya Shah	70000	IT
Amit Kumar	45000	NULL

Solution: John Doe and Rahul Patel satisfy both conditions.

Output:

EmployeeName	Salary	DepartmentName
John Doe	55000	Sales
Rahul Patel	60000	Sales

Q28: Write a query to list all customers who have placed orders worth more than $200. Use the Customers, Orders, and OrderDetails tables.
Answer
SELECT DISTINCT
    c.CustomerID,
    c.CustomerName
FROM Customers c
INNER JOIN Orders o
    ON c.CustomerID = o.CustomerID
INNER JOIN OrderDetails od
    ON o.OrderID = od.OrderID
GROUP BY
    c.CustomerID,
    c.CustomerName,
    o.OrderID
HAVING SUM(od.Quantity * od.UnitPrice) > 200;
Example with Solution

Input:

OrderID	CustomerID
1001	1
1002	2
1003	1

OrderDetails:

OrderID	Quantity	UnitPrice
1001	2	150
1002	1	100
1003	1	50

Solution:

Order 1001 = 2 × 150 = 300 → Greater than 200
Order 1002 = 1 × 100 = 100 → Not greater than 200
Order 1003 = 1 × 50 = 50 → Not greater than 200

Output:

CustomerID	CustomerName
1	Rahul

Q29: Write a query to find all employees who work in the "IT" department and have a salary greater than $60,000. Join the Employees and Departments tables and filter the results accordingly.
Answer
SELECT
    e.EmployeeName,
    e.Salary,
    d.DepartmentName
FROM Employees e
INNER JOIN Departments d
    ON e.DepartmentID = d.DepartmentID
WHERE d.DepartmentName = 'IT'
  AND e.Salary > 60000;
Example with Solution

Input:

EmployeeName	Salary	DepartmentName
Priya Shah	70000	IT
Rahul Patel	60000	Sales
John Doe	55000	Sales

Solution: Priya Shah is in IT and earns more than 60,000.

Output:

EmployeeName	Salary	DepartmentName
Priya Shah	70000	IT

Q30: Write a query to retrieve the name and address of all employees who are assigned to project "P123". Use the Employees and Projects tables.
Answer
SELECT
    e.EmployeeName,
    e.Address
FROM Employees e
INNER JOIN EmployeeProjects ep
    ON e.EmployeeID = ep.EmployeeID
INNER JOIN Projects p
    ON ep.ProjectID = p.ProjectID
WHERE p.ProjectID = 'P123';
Example with Solution

Input:

EmployeeProjects

EmployeeID	ProjectID
101	P123
102	P124

Projects

ProjectID	ProjectName
P123	Scholarship Portal
P124	AI Recommendation

Solution: John Doe is assigned to P123.

Output:

EmployeeName	Address
John Doe	Vadodara
7. JOIN with GROUP BY

Q31: Write a query to find the total number of orders for each customer. Group the results by customer.
Answer
SELECT
    c.CustomerName,
    COUNT(o.OrderID) AS TotalOrders
FROM Customers c
LEFT JOIN Orders o
    ON c.CustomerID = o.CustomerID
GROUP BY c.CustomerID, c.CustomerName;
Example with Solution

Input:

CustomerName	OrderID
Rahul	1001
Rahul	1003
Amit	1002
Priya	NULL

Solution:

Rahul has 2 orders
Amit has 1 order
Priya has 0 orders

Output:

CustomerName	TotalOrders
Rahul	2
Amit	1
Priya	0

Q32: Write a query to calculate the average salary for each department. Group the results by department name.
Answer
SELECT
    d.DepartmentName,
    AVG(e.Salary) AS AverageSalary
FROM Departments d
INNER JOIN Employees e
    ON d.DepartmentID = e.DepartmentID
GROUP BY d.DepartmentID, d.DepartmentName;
Example with Solution

Input:

DepartmentName	Salary
Sales	55000
Sales	60000
IT	70000

Solution:

Sales average = (55000 + 60000) / 2 = 57500
IT average = 70000 / 1 = 70000

Output:

DepartmentName	AverageSalary
Sales	57500
IT	70000

Q33: Write a query to find the total sales per product. Use the OrderDetails and Products tables and group the results by ProductID.
Answer
SELECT
    p.ProductID,
    p.ProductName,
    SUM(od.Quantity * od.UnitPrice) AS TotalSales
FROM Products p
INNER JOIN OrderDetails od
    ON p.ProductID = od.ProductID
GROUP BY p.ProductID, p.ProductName;
Example with Solution

Input:

ProductID	ProductName	Quantity	UnitPrice
1	Laptop	2	75000
2	Mouse	1	500
2	Mouse	2	500

Solution:

Laptop = 2 × 75000 = 150000
Mouse = (1 × 500) + (2 × 500) = 1500

Output:

ProductID	ProductName	TotalSales
1	Laptop	150000
2	Mouse	1500

Q34: Write a query to find the total number of employees in each department. Group the results by department name.
Answer
SELECT
    d.DepartmentName,
    COUNT(e.EmployeeID) AS TotalEmployees
FROM Departments d
LEFT JOIN Employees e
    ON d.DepartmentID = e.DepartmentID
GROUP BY d.DepartmentID, d.DepartmentName;
Example with Solution

Input:

DepartmentName	EmployeeName
Sales	John Doe
Sales	Rahul Patel
IT	Priya Shah
HR	NULL

Solution: Sales has 2 employees, IT has 1, and HR has 0.

Output:

DepartmentName	TotalEmployees
Sales	2
IT	1
HR	0

Q35: Write a query to calculate the average order amount for each customer. Group the results by customer.
Answer
SELECT
    c.CustomerName,
    AVG(order_totals.OrderAmount) AS AverageOrderAmount
FROM Customers c
INNER JOIN (
    SELECT
        o.OrderID,
        o.CustomerID,
        SUM(od.Quantity * od.UnitPrice) AS OrderAmount
    FROM Orders o
    INNER JOIN OrderDetails od
        ON o.OrderID = od.OrderID
    GROUP BY o.OrderID, o.CustomerID
) AS order_totals
    ON c.CustomerID = order_totals.CustomerID
GROUP BY c.CustomerID, c.CustomerName;
Example with Solution

Input:

CustomerID	CustomerName
1	Rahul
2	Amit

Order totals:

OrderID	CustomerID	OrderAmount
1001	1	300
1003	1	100
1002	2	500

Solution:

Rahul average = (300 + 100) / 2 = 200
Amit average = 500 / 1 = 500

Output:

CustomerName	AverageOrderAmount
Rahul	200
Amit	500
8. JOIN with Aggregate Functions

Q36: Write a query to find the highest priced product in each category. Join the Products and Categories tables and use the MAX function.
Answer
SELECT
    c.CategoryName,
    MAX(p.Price) AS HighestPrice
FROM Categories c
INNER JOIN Products p
    ON c.CategoryID = p.CategoryID
GROUP BY c.CategoryID, c.CategoryName;
Example with Solution

Input:

ProductName	CategoryID	Price
Laptop	1	75000
Mouse	1	500
Chair	2	5000

Solution:

Electronics → Highest price = 75000
Furniture → Highest price = 5000

Output:

CategoryName	HighestPrice
Electronics	75000
Furniture	5000

Q37: Write a query to find the total sales for each product. Join the Products and OrderDetails tables and calculate the total revenue for each product.
Answer
SELECT
    p.ProductName,
    SUM(od.Quantity * od.UnitPrice) AS TotalRevenue
FROM Products p
INNER JOIN OrderDetails od
    ON p.ProductID = od.ProductID
GROUP BY p.ProductID, p.ProductName;
Example with Solution

Input:

ProductName	Quantity	UnitPrice
Laptop	2	75000
Mouse	1	500
Mouse	2	500

Solution:

Laptop = 2 × 75000 = 150000
Mouse = 1 × 500 + 2 × 500 = 1500

Output:

ProductName	TotalRevenue
Laptop	150000
Mouse	1500


Q38: Write a query to find the minimum, maximum, and average price of products in each category. Use the Products and Categories tables and apply aggregate functions.
Answer
SELECT
    c.CategoryName,
    MIN(p.Price) AS MinimumPrice,
    MAX(p.Price) AS MaximumPrice,
    AVG(p.Price) AS AveragePrice
FROM Categories c
INNER JOIN Products p
    ON c.CategoryID = p.CategoryID
GROUP BY c.CategoryID, c.CategoryName;
Example with Solution

Input:

ProductName	CategoryID	Price
Laptop	1	75000
Mouse	1	500
Chair	2	5000

Solution:

Electronics:

Minimum = 500
Maximum = 75000
Average = (75000 + 500) / 2 = 37750

Furniture:

Minimum = 5000
Maximum = 5000
Average = 5000

Output:

CategoryName	MinimumPrice	MaximumPrice	AveragePrice
Electronics	500	75000	37750
Furniture	5000	5000	5000

Q39: Write a query to find the total number of employees in each department. Use the Employees and Departments tables and apply the COUNT function.
Answer
SELECT
    d.DepartmentName,
    COUNT(e.EmployeeID) AS TotalEmployees
FROM Departments d
LEFT JOIN Employees e
    ON d.DepartmentID = e.DepartmentID
GROUP BY d.DepartmentID, d.DepartmentName;
Example with Solution

Input:

DepartmentName	EmployeeID
Sales	101
Sales	103
IT	102
HR	NULL

Solution:

Sales = 2 employees
IT = 1 employee
HR = 0 employees

Output:

DepartmentName	TotalEmployees
Sales	2
IT	1
HR	0

Q40: Write a query to calculate the total amount of money spent on each order. Join the Orders and OrderDetails tables and use the SUM function.
Answer
SELECT
    o.OrderID,
    SUM(od.Quantity * od.UnitPrice) AS TotalOrderAmount
FROM Orders o
INNER JOIN OrderDetails od
    ON o.OrderID = od.OrderID
GROUP BY o.OrderID;
Example with Solution

Input:

OrderID	Quantity	UnitPrice
1001	2	75000
1001	1	500
1002	1	5000

Solution:

Order 1001 = (2 × 75000) + (1 × 500) = 150500
Order 1002 = 1 × 5000 = 5000

Output:

OrderID	TotalOrderAmount
1001	150500
1002	5000
9. JOIN with NULL Handling

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Q41: Write a query to find all students and the subjects they are enrolled in. If a student is not enrolled in any subject, show NULL for the subject.
Answer
SELECT
    s.StudentName,
    sub.SubjectName
FROM Students s
LEFT JOIN StudentSubjects ss
    ON s.StudentID = ss.StudentID
LEFT JOIN Subjects sub
    ON ss.SubjectID = sub.SubjectID;
Example with Solution

Input:

StudentID	StudentName
1	Rahul
2	Amit
3	Priya

StudentSubjects:

StudentID	SubjectID
1	1
1	2
3	3

Solution: Amit has no subject enrollment, so NULL is displayed.

Output:

StudentName	SubjectName
Rahul	DBMS
Rahul	AI
Amit	NULL
Priya	Networking

Q42: Write a query to retrieve all employees and their salaries, including those with NULL values. Join the Employees and Salary tables.
Answer
SELECT
    e.EmployeeName,
    s.SalaryAmount
FROM Employees e
LEFT JOIN Salary s
    ON e.EmployeeID = s.EmployeeID;
Example with Solution

Input:

Employees

EmployeeID	EmployeeName
101	John Doe
102	Priya Shah
103	Rahul Patel
104	Amit Kumar

Salary

EmployeeID	SalaryAmount
101	55000
102	70000
103	60000

Solution: Amit Kumar has no salary record, so NULL is displayed.

Output:

EmployeeName	SalaryAmount
John Doe	55000
Priya Shah	70000
Rahul Patel	60000
Amit Kumar	NULL

Q43: Write a query to list all orders and their status, showing NULL for orders without a status. Join the Orders and OrderStatus tables.
Answer
SELECT
    o.OrderID,
    os.StatusName
FROM Orders o
LEFT JOIN OrderStatus os
    ON o.Status = os.StatusID;
Example with Solution

Input:

Orders

OrderID	Status
1001	1
1002	2
1003	NULL

OrderStatus

StatusID	StatusName
1	Completed
2	Pending

Solution: Order 1003 has no status, so NULL is displayed.

Output:

OrderID	StatusName
1001	Completed
1002	Pending
1003	NULL

Q44: Write a query to find all customers and their phone numbers, displaying NULL where phone numbers are not available.
Answer
SELECT
    c.CustomerName,
    c.Phone
FROM Customers c;
Example with Solution

Input:

CustomerName	Phone
Rahul	9876543210
Amit	NULL
Priya	9123456780

Solution: Amit's phone number is missing, so NULL is displayed.

Output:

CustomerName	Phone
Rahul	9876543210
Amit	NULL
Priya	9123456780

Q45: Write a query to retrieve all products and their discount information, showing NULL for products without discounts.
Answer
SELECT
    p.ProductName,
    d.DiscountPercent
FROM Products p
LEFT JOIN Discounts d
    ON p.ProductID = d.ProductID;
Example with Solution

Input:

Products

ProductID	ProductName
1	Laptop
2	Mouse
3	Chair
4	Unknown Product

Discounts

ProductID	DiscountPercent
1	10
3	5

Solution: Laptop and Chair have discounts. Mouse and Unknown Product have no discount records.

Output:

ProductName	DiscountPercent
Laptop	10
Mouse	NULL
Chair	5
Unknown Product	NULL
