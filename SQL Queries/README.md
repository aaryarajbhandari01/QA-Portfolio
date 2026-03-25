### 🏟️ Sport Centre Database System – SQL Portfolio
## 📌 Project Overview

This project demonstrates the design and implementation of a relational database system for a Sport Centre. The system replaces a traditional file-based approach and enables efficient management of:

- Customers
- Staff & Managers
- Facilities
- Bookings
- Merchandise
- Orders

The goal is to ensure data integrity, efficient querying, and meaningful insights for business decision-making.

## 🧱 Database Design
## 🔗 Entities & Relationships

The database is designed using ERD and normalization (up to 3NF) to eliminate redundancy and maintain consistency.

📊 Core Tables
# 👤 Customer

Stores customer information.

- customer_id (PK)
- first_name, last_name
- age
- contact details

# 👨‍💼 Staff

Stores staff details.

- staff_id (PK)
- first_name, last_name
- position
- salary

# 🧑‍💼 Manager
Subclass of Staff (inherits staff_id)
Represents managerial roles

# 🏟️ Facility

Stores sport facilities.

- facility_id (PK)
- facility_name
- requirement
- price

# 📅 Booking

Links customers to facilities.

- booking_id (PK)
- customer_id (FK)
- facility_id (FK)
- booking_date
- booking_time
- status

# 🛍️ Merchandise

Stores items sold by the centre.

- merchandise_id (PK)
- merchandise_name
- price

# 📦 Orders

Stores customer orders.

- order_id (PK)
- customer_id (FK)
- staff_id (FK)

# 🔄 OrderMerch

Resolves many-to-many relationship between Orders and Merchandise.

- order_id (FK)
- merchandise_id (FK)

# 🔑 Key Relationships
- One Customer → Many Bookings
- One Facility → Many Bookings
- One Customer → Many Orders
- Many Orders ↔ Many Merchandise
- Staff → Manages Orders & Bookings
- Manager ⊂ Staff (Inheritance)
