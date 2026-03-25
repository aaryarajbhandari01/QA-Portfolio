# 📊 GROUP BY Queries

### Aggregation & Analysis

## Query 3: Booking count for specific date/time
SELECT COUNT(customerID) AS Booking_Count
FROM Booking
WHERE bookingDate = '2026-03-25' 
AND bookingTime = '10:00:00';

## Query 10: Salary statistics
SELECT MIN(salary) AS min_salary,
       MAX(salary) AS max_salary,
       AVG(salary) AS avg_salary
FROM Staff;

## Query 13: Total merchandise revenue
SELECT SUM(m.price * om.qty) AS total_revenue
FROM OrderMerch om
JOIN Merchandise m ON om.merchID = m.merchID;

## Query 14: Bookings per facility
SELECT f.facilityName, COUNT(b.bookingDate) AS total_bookings
FROM Booking b
JOIN Facility f ON b.facilityID = f.facilityID
GROUP BY f.facilityName;

