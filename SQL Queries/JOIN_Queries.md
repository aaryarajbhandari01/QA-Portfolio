# 🔗 JOIN Queries

### Relational Logic Across Multiple Tables

## Query 5: Average age of customers with bookings
SELECT AVG(age) AS AverageAge
FROM Customer c
JOIN Booking b ON c.customerID = b.customerID
WHERE b.bookingDate = '2026-03-25';

## Query 6: Customer bookings and orders (VIEW)
CREATE VIEW cus_booking_order AS
SELECT c.customerID, c.fName, c.lName, b.bookingDate, o.orderDate
FROM Customer c
LEFT JOIN Booking b ON c.customerID = b.customerID
LEFT JOIN [Order] o ON c.customerID = o.customerID;

SELECT * FROM cus_booking_order;

## Query 8: Customers with bookings or orders on Monday
SELECT DISTINCT c.fName, c.lName
FROM Customer c
LEFT JOIN Booking b ON c.customerID = b.customerID
LEFT JOIN [Order] o ON c.customerID = o.customerID
WHERE DATEPART(dw, b.bookingDate) = 2 
   OR DATEPART(dw, o.orderDate) = 2;

## Query 11: Customers with unconfirmed bookings
SELECT c.fName, c.lName, b.bStatus
FROM Booking b
JOIN Customer c ON b.customerID = c.customerID
WHERE b.bStatus != 'confirm';

## Query 12: Merchandise ordered by customer 1
SELECT c.fName, c.lName, m.merchName, om.qty
FROM OrderMerch om
JOIN [Order] o ON om.orderID = o.orderID
JOIN Merchandise m ON om.merchID = m.merchID
JOIN Customer c ON o.customerID = c.customerID
WHERE c.customerID = 1;
