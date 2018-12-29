
`ctrl+shift+m` for preview in atom


### Example, from w3schools
From  https://www.w3schools.com/sql/trysql.asp?filename=trysql_select_all
```
Customers : CustomerID, CustomerName, ContactName, Address, City, PostalCode, Country
Orders: OrderID, CustomerID, EmployeeID, OrderDate, ShipperID
```



```
SELECT Country, COUNT(Country) AS C FROM (SELECT Customers.CustomerID, Customers.Country, Orders.ShipperID FROM Customers JOIN Orders ON Orders.CustomerID=Customers.CustomerID) AS temp GROUP BY Country ORDER BY C DESC;
```




```
SELECT COUNT(DISTINCT) FROM (SELECT Customers.CustomerID
FROM Orders
JOIN Customers
ON Orders.CustomerID=Customers.CustomerID)
```


```
SELECT Country, City, COUNT(*) FROM (SELECT Customers.CustomerID, Customers.Country, Customers.City
FROM Orders
JOIN Customers
ON Orders.CustomerID=Customers.CustomerID) AS temp GROUP BY Country,City ORDER BY Country ASC, City DESC;
```

```
ORDER BY column1, column2, ... ASC|DESC;

ORDER BY Country ASC , City DESC;
```

```
SELECT SS, COUNT(*) as aaa FROM (SELECT Customers.CustomerID, Customers.Country AS SS
FROM Orders
JOIN Customers
ON Orders.CustomerID=Customers.CustomerID)
GROUP BY SS
ORDER BY aaa DESC, SS ASC;
```



```
SELECT DEPARTMENT.NAME, COUNT(*) AS COUNT_OF_STUDENTS_IN_THE_DEPARTMENT FROM (SELECT STUDENT.DEPT_ID, DEPARTMENT.ID, DEPARTMENT.NAME
FROM STUDENT
JOIN DEPARTMENT
ON STUDENT.DEPT_ID=DEPARTMENT.ID)
GROUP BY DEPARTMENT.NAME
ORDER BY COUNT_OF_STUDENTS_IN_THE_DEPARTMENT DESC, DEPARTMENT.NAME ASC;
```







### Write a SQL query to get the third highest salary of an employee from employee_table?

```
SELECT TOP 1 salary
FROM(
SELECT TOP 3 salary
FROM employee_table
ORDER BY salary DESC) AS temp
ORDER BY salary ASC;

```


### ROLL_NO BETWEEN|IN
```
SELECT * FROM Students where ROLL_NO BETWEEN 10 AND 50;

SELECT * FROM students where ROLL_NO IN (8,15,25);
```


###
What are the different set operators available in SQL?
Some of the available set operators are – Union, Intersect or Minus operators.



Select DISTINCT studentID from Student



### SUBSTRING
How can you fetch first 5 characters of the string?
There are a lot of ways to fetch characters from a string. For example:
```
Select SUBSTRING(StudentName,1,5) as studentname from student
```


### LIKE
```
SELECT * FROM Employees WHERE EmpName like 'A%' ;
```


### CREATE
```
CREATE TABLE Orders
(
O_ID int NOT NULL,
ORDER_NO int NOT NULL,
C_ID int,
PRIMARY KEY (O_ID),
FOREIGN KEY (C_ID) REFERENCES Customers(C_ID)
)
```


### DELETE
Delete duplicate data from table only first data remains constant.
```
DELETE M1
From managers M1, managers M2
Where M2.Name = M1.Name AND M1.Id>M2.Id;
```


### INSERT INTO
```
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```




### COALESCE
Finding the name of Employees where First Name, Second Name and Last Name is given in table. Some Name is missing such as First Name, Second Name and may be Last Name. Here we will use COALESCE() function which will return first Non Null values.


```
SELECT ID, COALESCE(FName, SName, LName) as Name
FROM employees;
```


### TIMESTAMPDIFF
Find the Employees who hired in the Last n months.

```
elect *, TIMESTAMPDIFF (month, Hiredate, current_date()) as DiffMonth
From employees
Where TIMESTAMPDIFF (month, Hiredate, current_date())
Between 1 and 5 Order by Hiredate desc;
```


### DATEDIFF
Find the Employees who hired in the Last n days.
```
Select *, DATEDIFF (current_date(), Hiredate) as DiffDay
From employees
Where DATEDIFF (current_date(), Hiredate) between 1 and 100 order by Hiredate desc;
```


### LEFT, like, substring
```
Select * From employees Where Fname like 'A%';

Select * From employees Where left(FName, 1)='A';

Select * From employees Where substring(FName, 1, 1)='A';
```








SELECT * INTO newtable FROM oldtable WHERE condition;





### UNION and UNION ALL
SELECT * FROM Table1
UNION
SELECT * FROM Table2



keeping all the duplictes
SELECT * FROM Table1
UNION ALL
SELECT * FROM Table2




##  add a column
How to add a column ‘Salary’ to a table Employee_Details?

ALTER TABLE Employee_Details ADD (Salary);



### List of All Tables From A DataBase

To view the tables available on a particular DataBase
```
USE TestDB
GO
SELECT * FROM sys.Tables
GO
```

### EXCEPT

How to fetch values from TestTable1 that are not in TestTable2 without using NOT keyword?

SELECT * FROM TestTable1 EXCEPT SELECT * FROM TestTable2;






###
What is the order of SQL SELECT?
Order of SQL SELECT statement is as follows

```
SELECT, FROM, WHERE, GROUP BY, HAVING, ORDER BY.
```




###
How to display the current date in SQL?

In SQL, there is a built-in function called GetDate() which helps to return the current date.

SELECT GetDate();


###
to select all the even number records from a table:

Select * from table where id % 2 = 0



### CASE
Can you display the result from the below table TestTable based on the criteria M,m as M and F, f as F and Null as N and g, k, I as U

```
SELECT Gender,
case
when Gender='i' then 'U'
when Gender='g' then 'U'
when Gender='H' then 'U'
when Gender='NULL' then 'N'
else upper(Gender)
end as newgender from TestTable GROUP BY Gender
```



### CASE
How do you update F as M and M as F from the below table TestTable?
UPDATE TestTable SET Gender = CASE Gender WHEN 'F' THEN 'M' ELSE 'F' END







### matt
SELECT col1 * (col2 + IFNULL(col3,0)) FROM Table1




#
