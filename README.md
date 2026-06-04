# Impact-DBMS

## 1. INNER JOIN

**Q1:** Write a query to retrieve the EmployeeName, EmployeeID, and DepartmentName for all employees who belong to a department. Join the Employees table with the Departments table.

**Q2:** Write a query to find the ProductName, CategoryName, and SupplierName for all products. Join the Products, Categories, and Suppliers tables.

**Q3:** Retrieve a list of all orders, along with their customer details (CustomerName, Address, Phone). Join the Orders and Customers tables.

**Q4:** Write a query to find the EmployeeName, Salary, and DepartmentName for all employees who work in the "Sales" department.

**Q5:** Write a query to list all products with their suppliers. Display ProductName and SupplierName. Join the Products and Suppliers tables.

## 2. LEFT JOIN (LEFT OUTER JOIN)

**Q6:** Write a query to retrieve all products and their categories. If a product is not assigned to any category, display NULL for the category.

**Q7:** Write a query to find all employees and their managers. If an employee doesn't have a manager, show NULL for the manager.

**Q8:** Write a query to list all customers and the orders they have placed. Show customers who haven't placed any order (i.e., include NULL for orders).

**Q9:** Write a query to find all employees along with their department details. Include employees who don't belong to any department (i.e., show NULL for department).

**Q10:** Write a query to display all students and the subjects they are enrolled in. If a student is not enrolled in any subject, show NULL for the subject.

## 3. RIGHT JOIN (RIGHT OUTER JOIN)

**Q11:** Write a query to list all products and the sales orders they belong to. Include all sales orders, even if no product is associated with the order.

**Q12:** Write a query to list all employees and the projects they are assigned to. Include all projects, even if no employees are assigned to them.

**Q13:** Write a query to retrieve all customers and their orders, including all orders even if no customer is associated with them.

**Q14:** Write a query to find all employees and the departments they belong to. Include all departments even if no employees belong to them.

**Q15:** Write a query to find all sales orders and the products associated with them. If a product is not associated with any order, show the order with NULL for the product.

## 4. FULL OUTER JOIN

**Q16:** Write a query to list all customers and their orders. Include all customers and all orders, even if a customer hasn't placed any orders or an order is placed by a non-existing customer.

**Q17:** Write a query to retrieve all employees and all projects. Include all employees and all projects, even if an employee is not assigned to a project or a project has no employees.

**Q18:** Write a query to list all students and all courses. If a student is not enrolled in any course or a course has no students, show NULL for the course or student.

**Q19:** Write a query to find all suppliers and products. Include all suppliers and all products, even if a supplier has no products or a product has no suppliers.

**Q20:** Write a query to list all orders and products. Include all orders and products, even if there are orders without products or products not ordered by anyone.

## 5. SELF JOIN

**Q21:** Write a query to find employees who work in the same department as "John Doe". Use the Employees table and join it with itself.

**Q22:** Write a query to list all employees and their managers. Use a self-join on the Employees table where the manager is an employee from the same table.

**Q23:** Write a query to find all employees who share the same department and have the same job title. Use the Employees table with a self-join.

**Q24:** Write a query to find all employees who report directly to the same manager. Join the Employees table with itself to find employees under the same manager.

**Q25:** Write a query to list all products that belong to the same category and have the same supplier. Join the Products table with itself on CategoryID and SupplierID.

## 6. JOIN with WHERE clause

**Q26:** Write a query to list all orders that were placed after January 1st, 2022. Join the Orders and Customers tables and filter by OrderDate.

**Q27:** Write a query to find all employees whose salary is greater than $50,000 and who belong to the "Sales" department. Join the Employees and Departments tables.

**Q28:** Write a query to list all customers who have placed orders worth more than $200. Use the Customers, Orders, and OrderDetails tables.

**Q29:** Write a query to find all employees who work in the "IT" department and have a salary greater than $60,000. Join the Employees and Departments tables and filter the results accordingly.

**Q30:** Write a query to retrieve the name and address of all employees who are assigned to project "P123". Use the Employees and Projects tables.

## 7. JOIN with GROUP BY

**Q31:** Write a query to find the total number of orders for each customer. Group the results by customer.

**Q32:** Write a query to calculate the average salary for each department. Group the results by department name.

**Q33:** Write a query to find the total sales per product. Use the OrderDetails and Products tables and group the results by ProductID.

**Q34:** Write a query to find the total number of employees in each department. Group the results by department name.

**Q35:** Write a query to calculate the average order amount for each customer. Group the results by customer.

## 8. JOIN with Aggregate Functions

**Q36:** Write a query to find the highest priced product in each category. Join the Products and Categories tables and use the MAX function.

**Q37:** Write a query to find the total sales for each product. Join the Products and OrderDetails tables and calculate the total revenue for each product.

**Q38:** Write a query to find the minimum, maximum, and average price of products in each category. Use the Products and Categories tables and apply aggregate functions.

**Q39:** Write a query to find the total number of employees in each department. Use the Employees and Departments tables and apply the COUNT function.

**Q40:** Write a query to calculate the total amount of money spent on each order. Join the Orders and OrderDetails tables and use the SUM function.

## 9. JOIN with NULL Handling

**Q41:** Write a query to find all students and the subjects they are enrolled in. If a student is not enrolled in any subject, show NULL for the subject.

**Q42:** Write a query to retrieve all employees and their salaries, including those with NULL values. Join the Employees and Salary tables.

**Q43:** Write a query to list all orders and their status, showing NULL for orders without a status. Join the Orders and OrderStatus tables.

**Q44:** Write a query to find all customers and their phone numbers, displaying NULL where phone numbers are not available.

**Q45:** Write a query to retrieve all products and their discount information, showing NULL for products without discounts.
