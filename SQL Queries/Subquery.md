# 🧠 Subqueries 


## Customers with no bookings
SELECT fName, lName
FROM Customer
WHERE customerID NOT IN (
    SELECT customerID FROM Booking
);

## Facilities with no bookings
SELECT facilityName
FROM Facility
WHERE facilityID NOT IN (
    SELECT facilityID FROM Booking
);

