# 📄 SELECT Queries

### Basic Data Retrieval, Filtering, Ordering


## Query 1 (Part): Facility count
SELECT COUNT(*) AS total_facilities FROM Facility;

## Query 1 (Part): Facility names and prices
SELECT facilityName, price FROM Facility;

## Query 2: Facilities with requirements and prices
SELECT facilityName, requirement, price FROM Facility;

## Query 4: Merchandise and prices
SELECT merchName, price FROM Merchandise;

## Query 7: Bookings on Monday
SELECT *
FROM Booking
WHERE DATEPART(dw, bookingDate) = 2;

## Query 9: Staff names and roles
SELECT fName, lName, role FROM Staff;



