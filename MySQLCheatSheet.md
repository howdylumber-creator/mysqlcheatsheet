### How to login into MySQL from terminal

#sudo mysql -u root

### How to SHOW USERS
#SELECT USER, HOST, Password FROM mysql.user;

### How to CREATE USERS
# CREATE USER 'new_user'@'localhost' IDENTIFIED BY 'secure_password';

### How to GRANT PRIVILEGES, Show granted privileges and remove.
# GRANT ALL PRIVILEGES ON database_name.* TO 'username'@'localhost';
# REVOKE ALL PRIVILEGES ON database_name.* FROM 'username'@'localhost';
 
### How to SHOW, DELETE & CREATE DATABASES & SELECT DATABASES
# SHOW DATABASES;
# CREATE DATABASE database_name;
# DROP DATABASE database_name; 

### How to CREATE a TABLE with Columns and their data types
"	CREATE TABLE table_name (
		column1 datatype constraints,
		column2 datatype constraints,
		column3 datatype constraints,
		...
	);
or
"       CREATE TABLE Clients (
                clientID INT PRIMARY KEY,
		FirstName VARCHAR(50),
		LastName VARCHAR(50),
		ProjectName Name
		ProjectDate DATE
        );

### How to SHOW, DELETE & DROP Tables
#Show 
	SELECT * FROM INFORMATION_SCHEMA.TABLES WHERE table_schema = 'your_database_name';
#DELECT
	DELECT FROM table_name;
	DELECT FROM table_name WHERE condition;
#DROP: permanently remove an entire table from the database.
	DROP TABLE table_name;
	DROP TABLE table_name CASCADE;

### How to Insert ROWS & RECORDS (single and multiple)
#single
	INSERT INTO table_name(column1) VALES (values1, values 2, values 3);
	INSERT INTO Clients (ClientName, ClientNumber, ProjectName) VALUES ('Ella Mushin', 123-123-123, 'A ski video');
#Multiple
	INSERT INTO table_name (column1, column2, column3) VALUES
	(valueA1, valuesA2, valuesA3),
	(valueB1, valuesB2, valuesB3),
	(valueC1, valuesC2, valuesC3);

	INSER INTO Clients (ClientName, ClientNumber, ProjectName) VALUES
	('Ella Mushin', 123-123-123, 'A ski video'),
	('Jessie Liu', 321-321-321, 'A docmentary about her obession with Sony'),
	('Genevieve Nadeau', 456-456-456, 'A snowboarding video');
	
### How to SELECT with the WHERE Clause
#SELECT * FROM Clients WHERE Project = 'video';

### How to SELECT with the WHERE Clause using a range
# SELECT column-name(s) FROM table_name WHERE column_name BETWEEN values1 AND values2;
# Numeric Range
	SELECT Name, Price FROM Projects WHERE ProjectPrive BETWEEN 500 and 1000;
# Date Range
	SELECT * FROM Projects where ProjectDate BETWEEN '2025-05-01' AND '2026-01-31';

### How to DELETE an individual ROW
	DELECT FROM table_name WHERE condition;
	DELECT FROM Products WHERE product_name = 'shoes';

### How to UPDATE a ROW
	UPDATE table_name SET column1 = value1, colum2 = value 2, WHERE condition;
	UPDATE Customers SET email = 'wecare@insurance.com' WHERE customer_id = 34;

### How to add a new column and modify it
	ALTER TABLE table_name ADD COLUMN column_name data_type constraint;
	ALTER TABLE Customers ADD COLUMN email VARCHAR(100);
 
### How to Order by and use Distinct
# SELECT DISTINCT to retrieve unique values and the ORDER BY clause to sort the results
	SELECT DISTINCT column1, column2, FROM table_name WHERE condition ORDER BY column_nane [ASC|DESC]
	SELECT DISTINCT Country FROM Products ORDER BY Country ASC;

### How to Concatenate Columns
	SELECT CONCAT(first_name, ' ', last_name) AS full_name FROM clients;	

### How to Select Distinct Rows
	SELECT DISTINCT column1, column2 FROM table_names;
	SELECT DISTINCT country FROM customers;
	Select DISTINCT first_name, last_name FROM employees;

### How to use LIKE to Search
	SELECT column1, column2, FROM table_name WHERE columnN LIKE pattern;
	SELECT * FROM table_name WHERE CustomerName LIKE 'A%'; 
	
	A%, %a, %r%, a_%, a%o, A%

### How to Select using IN
	SELECT * FROM populations WHERE Country IN ('Canada', 'England','France');

### How to Create & Remove Index
	CREATE INDEX idx_lastname ON Persons (lastName);
	DROP INDEX index_name ON table_name;

### Create Two Tables demonstrating a one to many relationship that shows a PK & FK
# Primary Key (PK): unique identifier for a record ( customerID)
101, 102, 102 
# Foreign Key (FK): A column in the "many table that refers to the Primary Key in the "one"table.
1,2,3,4,5
#one side table
	CREATE TABLE Customers (
		CustomerID INT PRIMARY KEY,
		CustomerName VARCHAR(100),
		Email VARCHAR(100)
	);
#Many side table
	CREATE TABLE Orders(
		OrderID INT PRIMARY KEY,
		OrderDate DATE,
		TotalAmount DECIMAL(10,2),
		CustomerID INT,
		FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
	);


### How to use Inner Join
...to specify the two (or more) tables you want to combine and the common column(s) on which to match the rows using the ON clause.

	SELECT column1, column2, FROM table1 INNER JOIN table2 ON table1.column_name = table2.column_name;

### How to JOIN Multiple Tables
	SELECT C.CustomerName, O.OrderID, S.Status
	FROM Customers AS C
	INNER JOIN Orders AS O ON C.CustomerID = O.CustomerID
	INNER JOIN Shippings AS S ON O.ShipperID = S.ShipperID;
