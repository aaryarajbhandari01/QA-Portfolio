# 🏟️ Sport Centre Database System – SQL Queries

## 🔗 Project Resources

- 📊 **Diagram**: [View Context, DFD, ERD, and GRD Diagram]([https://github.com/aaryarajbhandari01/QA-Portfolio/tree/main/SQL%20Queries/docs])
- 📄 **Project Documentation**: [View Full Documentation]([https://github.com/aaryarajbhandari01/QA-Portfolio/blob/main/SQL%20Queries/docs/Project%20Documentation.md])


## 📌 Table of Contents
1. [Table Creation Queries](#1-table-creation-queries)
2. [Insert Sample Data](#2-insert-sample-data)
3. [SQL Queries with Results](#3-sql-queries-with-results)
   - [Query 1: Facilities Count, Names & Prices](#query-1-how-many-facilities-their-names-and-prices)
   - [Query 2: Facilities Requirement & Prices](#query-2-list-all-facilities-their-requirement-and-prices)
   - [Query 3: Customers Booked on Specific Date & Time](#query-3-customers-with-bookings-for-a-specific-date-time)
   - [Query 4: Merchandise & Prices](#query-4-merchandise-and-their-prices)
   - [Query 5: Average Customer Age](#query-5-average-age-of-customers-who-booked-on-2026-03-25)
   - [Query 6: Customer Bookings & Orders](#query-6-customer-names-with-bookings-and-orders)
   - [Query 7: Bookings on Monday](#query-7-bookings-on-monday-datepart-dw2)
   - [Query 8: Customers with Bookings or Orders on Monday](#query-8-customers-with-bookings-or-orders-on-monday)
   - [Query 9: Staff Names & Roles](#query-9-staff-names-and-roles)
   - [Query 10: Staff Salary Statistics](#query-10-min-max-and-average-staff-salaries)
   - [Query 11: Unconfirmed Bookings](#query-11-customers-with-unconfirmed-bookings)
   - [Query 12: Merchandise Ordered by Customer 1](#query-12-merchandise-ordered-by-customer-1)
   - [Query 13: Total Merchandise Revenue](#query-13-total-revenue-from-merchandise-orders)
   - [Query 14: Bookings Per Facility](#query-14-number-of-bookings-per-facility)

---

## 1️⃣ Table Creation Queries

```sql
-- Customer Table
CREATE TABLE Customer (
    customerID INT PRIMARY KEY,
    fName VARCHAR(15),
    lName VARCHAR(15),
    email VARCHAR(35) UNIQUE,
    age INT,
    phoneNo VARCHAR(15) NOT NULL
);

-- Staff Table
CREATE TABLE Staff (
    staffID INT PRIMARY KEY,
    fName VARCHAR(15),
    lName VARCHAR(15),
    role VARCHAR(15),
    salary DECIMAL CHECK(salary > 0),
    phoneNo VARCHAR(15)
);

-- Manager Table
CREATE TABLE Manager (
    staffID INT PRIMARY KEY,
    department VARCHAR(15),
    FOREIGN KEY (staffID) REFERENCES Staff(staffID)
);

-- Facility Table
CREATE TABLE Facility (
    facilityID INT PRIMARY KEY,
    facilityName VARCHAR(30) NOT NULL,
    location VARCHAR(15),
    description VARCHAR(250),
    requirement VARCHAR(30),
    price INT NOT NULL
);

-- Merchandise Table
CREATE TABLE Merchandise (
    merchID INT PRIMARY KEY,
    merchName VARCHAR(15) NOT NULL,
    description VARCHAR(250),
    price INT
);

-- Order Table
CREATE TABLE [Order] (
    orderID INT PRIMARY KEY,
    status VARCHAR(15) CHECK(status IN ('pending', 'confirm', 'cancelled')),
    orderDate DATE,
    customerID INT,
    FOREIGN KEY (customerID) REFERENCES Customer(customerID)
);

-- OrderMerch Table
CREATE TABLE OrderMerch (
    orderID INT,
    merchID INT,
    qty INT,
    PRIMARY KEY(orderID, merchID),
    FOREIGN KEY (orderID) REFERENCES [Order](orderID),
    FOREIGN KEY (merchID) REFERENCES Merchandise(merchID)
);

-- Booking Table
CREATE TABLE Booking (
    bookingDate DATE,
    bookingTime TIME,
    bStatus VARCHAR(15) CHECK(bStatus IN ('pending', 'confirm', 'cancelled')),
    facilityID INT,
    customerID INT,
    staffID INT,
    PRIMARY KEY(bookingDate, bookingTime, facilityID, customerID, staffID),
    FOREIGN KEY (facilityID) REFERENCES Facility(facilityID),
    FOREIGN KEY (customerID) REFERENCES Customer(customerID),
    FOREIGN KEY (staffID) REFERENCES Staff(staffID)
);
````

---

## 2️⃣ Insert Sample Data

```sql
-- Customers
INSERT INTO Customer VALUES
(1, 'Alice', 'Smith', 'alice.smith@email.com', 28, '0412345678'),
(2, 'Bob', 'Johnson', 'bob.johnson@email.com', 32, '0423456789');

-- Staff
INSERT INTO Staff VALUES
(1, 'David', 'Brown', 'Trainer', 65000, '0412333444'),
(2, 'Emma', 'Davis', 'Receptionist', 50000, '0412444555');

-- Manager
INSERT INTO Manager VALUES
(1, 'Operations');

-- Facilities
INSERT INTO Facility VALUES
(1, 'Tennis Court', 'Ground Floor', 'Indoor court with lights', 'Racket required', 50),
(2, 'Swimming Pool', 'First Floor', 'Olympic size pool', 'Swimwear required', 30);

-- Merchandise
INSERT INTO Merchandise VALUES
(1, 'Tennis Racket', 'Professional tennis racket', 120),
(2, 'Swimming Goggles', 'Anti-fog goggles', 25);

-- Orders
INSERT INTO [Order] VALUES
(1, 'confirm', '2026-03-20', 1),
(2, 'pending', '2026-03-21', 2);

-- OrderMerch
INSERT INTO OrderMerch VALUES
(1, 1, 2),
(2, 2, 1);

-- Bookings
INSERT INTO Booking VALUES
('2026-03-25', '09:00:00', 'cancelled', 1, 1, 1),
('2026-03-25', '10:00:00', 'confirm', 2, 2, 2);
```

---

## 3️⃣ SQL Queries with Results

### Query 1: How many facilities, their names and prices

```sql
SELECT COUNT(*) AS total_facilities FROM Facility;
SELECT facilityName, price FROM Facility;
```

| total_facilities |
| ---------------- |
| 2                |

| facilityName  | price |
| ------------- | ----- |
| Tennis Court  | 50    |
| Swimming Pool | 30    |

---

### Query 2: List all facilities, their requirement, and prices

```sql
SELECT facilityName, requirement, price FROM Facility;
```

| facilityName  | requirement       | price |
| ------------- | ----------------- | ----- |
| Tennis Court  | Racket required   | 50    |
| Swimming Pool | Swimwear required | 30    |

---

### Query 3: Customers with bookings for a specific date & time

```sql
SELECT COUNT(customerID) AS Booking_Count
FROM Booking
WHERE bookingDate = '2026-03-25' AND bookingTime = '10:00:00';
```

| Booking_Count |
| ------------- |
| 1             |

---

### Query 4: Merchandise and their prices

```sql
SELECT merchName, price FROM Merchandise;
```

| merchName        | price |
| ---------------- | ----- |
| Tennis Racket    | 120   |
| Swimming Goggles | 25    |

---

### Query 5: Average age of customers who booked on 2026-03-25

```sql
SELECT AVG(age) AS AverageAge
FROM Customer c
JOIN Booking b ON c.customerID = b.customerID
WHERE b.bookingDate = '2026-03-25';
```

| AverageAge |
| ---------- |
| 30         |

---

### Query 6: Customer names with bookings and orders

```sql
CREATE VIEW cus_booking_order AS
SELECT c.customerID, c.fName, c.lName, b.bookingDate, o.orderDate
FROM Customer c
LEFT JOIN Booking b ON c.customerID = b.customerID
LEFT JOIN [Order] o ON c.customerID = o.customerID;

SELECT * FROM cus_booking_order;
```

| customerID | fName | lName   | bookingDate | orderDate  |
| ---------- | ----- | ------- | ----------- | ---------- |
| 1          | Alice | Smith   | 2026-03-25  | 2026-03-20 |
| 2          | Bob   | Johnson | 2026-03-25  | 2026-03-21 |

---

### Query 7: Bookings on Monday (DATEPART dw=2)

```sql
SELECT *
FROM Booking
WHERE DATEPART(dw, bookingDate) = 2;
```

| bookingDate | bookingTime | bStatus   | facilityID | customerID | staffID |
| ----------- | ----------- | --------- | ---------- | ---------- | ------- |
| 2026-03-25  | 09:00:00    | cancelled | 1          | 1          | 1       |
| 2026-03-25  | 10:00:00    | confirm   | 2          | 2          | 2       |

---

### Query 8: Customers with bookings or orders on Monday

```sql
SELECT DISTINCT c.fName, c.lName
FROM Customer c
LEFT JOIN Booking b ON c.customerID = b.customerID
LEFT JOIN [Order] o ON c.customerID = o.customerID
WHERE DATEPART(dw, b.bookingDate) = 2 OR DATEPART(dw, o.orderDate) = 2;
```

| fName | lName   |
| ----- | ------- |
| Alice | Smith   |
| Bob   | Johnson |

---

### Query 9: Staff names and roles

```sql
SELECT fName, lName, role FROM Staff;
```

| fName | lName | role         |
| ----- | ----- | ------------ |
| David | Brown | Trainer      |
| Emma  | Davis | Receptionist |

---

### Query 10: Min, Max, Average staff salaries

```sql
SELECT MIN(salary) AS min_salary, MAX(salary) AS max_salary, AVG(salary) AS avg_salary
FROM Staff;
```

| min_salary | max_salary | avg_salary |
| ---------- | ---------- | ---------- |
| 50000      | 65000      | 57500      |

---

### Query 11: Customers with unconfirmed bookings

```sql
SELECT c.fName, c.lName, b.bStatus
FROM Booking b
JOIN Customer c ON b.customerID = c.customerID
WHERE b.bStatus != 'confirm';
```

| fName | lName | bStatus   |
| ----- | ----- | --------- |
| Alice | Smith | cancelled |

---

### Query 12: Merchandise ordered by customer 1

```sql
SELECT c.fName, c.lName, m.merchName, om.qty
FROM OrderMerch om
JOIN [Order] o ON om.orderID = o.orderID
JOIN Merchandise m ON om.merchID = m.merchID
JOIN Customer c ON o.customerID = c.customerID
WHERE c.customerID = 1;
```

| fName | lName | merchName     | qty |
| ----- | ----- | ------------- | --- |
| Alice | Smith | Tennis Racket | 2   |

---

### Query 13: Total revenue from merchandise orders

```sql
SELECT SUM(m.price * om.qty) AS total_revenue
FROM OrderMerch om
JOIN Merchandise m ON om.merchID = m.merchID;
```

| total_revenue |
| ------------- |
| 265           |

---

### Query 14: Number of bookings per facility

```sql
SELECT f.facilityName, COUNT(b.bookingDate) AS total_bookings
FROM Booking b
JOIN Facility f ON b.facilityID = f.facilityID
GROUP BY f.facilityName;
```

| facilityName  | total_bookings |
| ------------- | -------------- |
| Tennis Court  | 1              |
| Swimming Pool | 1              |

---

