# ✏️ INSERT / UPDATE / DELETE Queries



## Insert Customer
```sql
INSERT INTO Customer VALUES
(1, 'Alice', 'Smith', 'alice.smith@email.com', 28, '0412345678'),
(2, 'Bob', 'Johnson', 'bob.johnson@email.com', 32, '0423456789');
```

## Insert Staff
```sql
INSERT INTO Staff VALUES
(1, 'David', 'Brown', 'Trainer', 65000, '0412333444'),
(2, 'Emma', 'Davis', 'Receptionist', 50000, '0412444555');
```

## Insert Booking
```sql
INSERT INTO Booking VALUES
('2026-03-25', '09:00:00', 'cancelled', 1, 1, 1),
('2026-03-25', '10:00:00', 'confirm', 2, 2, 2);
```

## Example Update
```sql
UPDATE Booking
SET bStatus = 'confirm'
WHERE bStatus = 'pending';
```

## Example Delete
```sql
DELETE FROM Booking
WHERE bStatus = 'cancelled';
```
