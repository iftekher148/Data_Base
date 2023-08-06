# Data_Base

### Create a table name Employee 
      CREATE TABLE EMPLOYEE (
    EMPLOYEE_ID int,
    LAST_NAME varchar(255),
    FIRST_NAME varchar(255),
    MIDDLE_NAME varchar(255),
    JOB_ID INT,
    MANAGER_ID INT,
    HIRE_DATE DATETIME,
    SALARY INT,
    COMM INT,
    DEPARTMENT_ID INT,
    PRIMARY KEY (EMPLOYEE_ID),
    FOREIGN KEY (JOB_ID) REFERENCES JOB(JOB_ID),
    FOREIGN KEY (DEPARTMENT_ID) REFERENCES DEPARTMENT(DEPARTMENT_ID)
    );

     INSERT INTO EMPLOYEE VALUES
	  (7369, 'SMITH', 'JOHN', 'Q', 667, 7902, '17-Dec-84', 800, NULL, 20),
    (7499, 'ALLEN', 'KEVIN', 'J', 670, 7698, '20-Feb-85', 1600, 300, 30),
    (7505, 'DOYLE', 'JEAN', 'K', 671, 7839, '4-Apr-85', 2850, NULL, 30),
    (7506, 'DENNIS', 'LYNN', 'S', 671, 7839, '15-May-85', 2750, NULL, 30),
    (7507, 'BAKER', 'LESLIE', 'D', 671, 7839, '10-Jun-85', 2200, NULL, 40),
    (7521, 'WARK', 'CYNTHIA', 'D', 670, 7698, '22-Feb-85', 1250, NULL, 40);

#### Fetch all columns from the Employee table:
      SELECT * from EMPLOYEE;
![image](https://github.com/iftekher148/Data_Base/assets/37367596/6d469958-e9ce-44c0-8c08-5eb7cb86ffdf)

#### Fetch last_name, first_name, salary of Employee
      SELECT last_name, first_name, salary
       FROM EMPLOYEE;
![image](https://github.com/iftekher148/Data_Base/assets/37367596/bb4a523b-dea6-46a7-bfd0-276008a15358)

#### Fetch all different/distinct JOB_Id of the Employee table
      SELECT DISTINCT job_id from EMPLOYEE;
![image](https://github.com/iftekher148/Data_Base/assets/37367596/a160da05-8a40-4b66-a0b2-46dfb58e5a85)

#### Fetch the details of David's employee from Employee.
      SELECT * FROM Employee WHERE name='David'
![image](https://github.com/iftekher148/Data_Base/assets/37367596/ddf171b2-bc53-4bf8-be44-8bffbdf8b381)

#### Fetch details of employees that their salary is neither '800' nor '1250'.
      SELECT * FROM Employee 
      WHERE salary != 800
      AND salary != 1250
![image](https://github.com/iftekher148/Data_Base/assets/37367596/bb76b04d-bcc7-4dbb-8262-16ac741b0e2c)

#### Fetch names of employees that start with a 'D' or end with an 'N'
      SELECT * FROM Employee 
      WHERE last_name LIKE 'D%'
      OR  last_name LIKE '%N'
![image](https://github.com/iftekher148/Data_Base/assets/37367596/d5554d1e-341d-4aac-8486-8cc28665c63b)

#### Fetch names of employers that have a salary between 800 and 1500.
      SELECT first_name,last_name 
      FROM Employee 
      WHERE salary 
      BETWEEN 800 and 1500;
![image](https://github.com/iftekher148/Data_Base/assets/37367596/591fbd7a-52b1-47d3-b573-894dca354dc2)

#### Fetch job_id, and manager_id sorted by the manager_id column in the default ascending order:
      SELECT job_id, manager_id from EMPLOYEE ORDER by manager_id ASC
![image](https://github.com/iftekher148/Data_Base/assets/37367596/ca0a2ad8-3845-404e-91ad-8bfa29c6b9e5)
  
#### Fetch data of Employees from the first 3.
       SELECT * from EMPLOYEE LIMIT 3
![image](https://github.com/iftekher148/Data_Base/assets/37367596/7b1158ce-07f7-4c9a-befd-9553623d4511)

#### Find out the Highest and Lowest salary from employees
        SELECT MAX(salary) AS HighestSalary,
        MIN (Salary) AS LowestSaraly
        from EMPLOYEE
![image](https://github.com/iftekher148/Data_Base/assets/37367596/afed0756-754a-4c71-bbf6-a597026fd39d)

#### Find out the 2nd Highest salary from employees
      SELECT MAX(salary) As secondHigh
      from EMPLOYEE
      WHERE salary < (SELECT MAX(salary) FROM EMPLOYEE)
![image](https://github.com/iftekher148/Data_Base/assets/37367596/c68c319e-3ba8-482b-b5b8-453ef0ff91eb)

#### Find out the number of employees:
      SELECT COUNT(*)
      from EMPLOYEE;
![image](https://github.com/iftekher148/Data_Base/assets/37367596/845d8d1d-2af7-48b4-8ccc-c440e8a93a95)


## DB_Table-1:Customers
  ![image](https://github.com/iftekher148/Data_Base/assets/37367596/55450dac-dbdf-4bc9-8495-a3ff393eea8a)

## DB_Table-2:Suppliers
  ![image](https://github.com/iftekher148/Data_Base/assets/37367596/abba7868-8f17-4a20-a2ba-4a077ae62845)

#### Fetch the cities from both the "Customers" and the "Suppliers" table:
    SELECT City FROM Customers
    UNION ALL
    SELECT City FROM Suppliers
    ORDER BY City;
![image](https://github.com/iftekher148/Data_Base/assets/37367596/5f29fe06-92d4-4159-85bd-d9ac0d0b78c9)

#### Lists all customers and suppliers in a one table
      SELECT 'Customer' AS Type, ContactName, City, Country
      FROM Customers
      UNION
      SELECT 'Supplier', ContactName, City, Country
      FROM Suppliers
![image](https://github.com/iftekher148/Data_Base/assets/37367596/4bb884a7-592a-4e16-b535-3dadfa7cb5f3)

#### Lists the number of customers in each country.
    SELECT COUNT(CustomerID), Country
    FROM Customers
    GROUP BY Country;
![image](https://github.com/iftekher148/Data_Base/assets/37367596/81bdf02e-b298-4b9d-83be-6b1e231020f3)

#### Lists the number of customers in each country, sorted high to low.
      SELECT COUNT(CustomerID), Country 
      FROM Customers 
      GROUP BY Country 
      ORDER BY COUNT(CustomerID) DESC
![image](https://github.com/iftekher148/Data_Base/assets/37367596/6c7834c9-2c16-4a8f-9c8f-9c5b92230b4f)

#### Lists the number of customers in each country. Only include countries with more than 5 customers.
      SELECT COUNT(CustomerID), Country 
      FROM Customers 
      GROUP BY Country 
      HAVING COUNT(CustomerID) > 5;
![image](https://github.com/iftekher148/Data_Base/assets/37367596/a76b979a-5957-4c38-ba8a-e947861924e1)

## DB_Table-1:Orders
  ![image](https://github.com/iftekher148/Data_Base/assets/37367596/42e2a954-57a9-4f16-94b4-9f2a845912c5)
## DB_Table-2:Customers
  ![image](https://github.com/iftekher148/Data_Base/assets/37367596/f7c0191b-3a6b-4dd1-a01d-60b523351c64)

#### Fetch OrderID, CustomerName, ContactName, and OrderDate from two tables.
      SELECT Orders.OrderID, Customers.CustomerName, Customers.ContactName, Orders.OrderDate
      FROM Orders
      INNER JOIN Customers
      ON Orders.CustomerID = Customers.CustomerID;
  ![image](https://github.com/iftekher148/Data_Base/assets/37367596/b678edb4-c14f-414e-8a01-254f187e28b7)
    
#### Fetch CustomerName, ContactName,from customer(left) table and OrderDate(right) from Orders table.
      SELECT Customers.CustomerName, Customers.ContactName, Orders.OrderDate
      FROM Customers
      LEFT JOIN Orders
      ON Customers.CustomerID=Orders.CustomerID
![image](https://github.com/iftekher148/Data_Base/assets/37367596/55e81f61-0c5f-46b3-b5b1-babb61ef05d4)

## DB_Table-1:Orders
![image](https://github.com/iftekher148/Data_Base/assets/37367596/3370b3fb-51b2-463d-b7c1-86c7346dad12)
## DB_Table-2:Shippers
![image](https://github.com/iftekher148/Data_Base/assets/37367596/c42ea1ef-ec6f-4ca8-a484-32d1062e969e)
## DB_Table-3:Employees
![image](https://github.com/iftekher148/Data_Base/assets/37367596/c799bfba-1050-4579-8f38-a336516e4cf9)


#### Lists the number of orders sent by each shipper.
      SELECT COUNT(Orders.OrderID) AS TotalOrder, Shippers.ShipperName
      FROM Orders
      LEFT JOIN Shippers
      ON Orders.ShipperID = Shippers.ShipperID
      GROUP BY ShipperName
![image](https://github.com/iftekher148/Data_Base/assets/37367596/9bda36ad-2aab-4db9-9345-1d486ea235c2)

####  Lists the employees(t-3) that have registered more than 10 orders(t-1):
      SELECT COUNT(Orders.OrderID) AS NumberOfOrder, Employees.LastName 
      FROM Orders 
      INNER JOIN Employees 
      ON Orders.EmployeeID = Employees.EmployeeID 
      GROUP BY LastName 
      HAVING COUNT(Orders.OrderID) > 10
![image](https://github.com/iftekher148/Data_Base/assets/37367596/237d5eb9-6d2d-4807-b27d-60beefbaa245)

#### Lists if the employees "Davolio" or "Fuller" have registered more than 25 orders.
      SELECT COUNT(Orders.OrderID) AS NumberOfOrder, Employees.LastName
      FROM Orders
      INNER JOIN Employees
      ON Orders.EmployeeID = Employees.EmployeeID
      WHERE LastName = 'Davolio' OR LastName = 'Fuller'
      GROUP BY LastName
      HAVING COUNT(Orders.OrderID) > 25
![image](https://github.com/iftekher148/Data_Base/assets/37367596/78ef78c4-cde4-4adf-a4ca-efd541185e04)

#### Update Customers table with name 'BugsBD' and address 'Dhaka,Bangladesh'
      UPDATE Customers
      SET CustomerName= 'BugsBD', Address='Dhaka,Bangladesh'
      WHERE CustomerID=2;
![image](https://github.com/iftekher148/Data_Base/assets/37367596/6f2f1169-63d2-4935-a7ea-22085880856b)

#### Delete 'BugsDB' row from Customers table.
      DELETE FROM Customers WHERE CustomerName='BugsBD';
![image](https://github.com/iftekher148/Data_Base/assets/37367596/aeeaeb44-874f-4fdb-9cbb-599b83e691b3)











