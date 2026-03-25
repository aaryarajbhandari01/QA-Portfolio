# Error Scenarios (QA Testing)

### Invalid Queries & Constraint Testing

## Duplicate Primary Key
INSERT INTO Customer VALUES
(1, 'Duplicate', 'User', 'dup@email.com', 25, '0400000000');

## Foreign Key Violation
INSERT INTO Booking VALUES
('2026-03-26', '11:00:00', 'confirm', 99, 99, 99);

## CHECK Constraint Violation
INSERT INTO Staff VALUES
(3, 'Test', 'User', 'Trainer', -5000, '0400000000');

## NULL Violation
INSERT INTO Customer (customerID, fName)
VALUES (NULL, 'Invalid');

## Invalid Column
SELECT non_existing_column FROM Customer;
