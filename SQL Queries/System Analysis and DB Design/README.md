
### 🏟️ Sport Centre Database System – Sample System Analysis and Database Design Project for SQL Queries
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

# 📊 Core Tables
## 👤 Customer

Stores customer information.

- customer_id (PK)
- first_name, last_name
- age
- contact details

## 👨‍💼 Staff

Stores staff details.

- staff_id (PK)
- first_name, last_name
- position
- salary

## 🧑‍💼 Manager
Subclass of Staff (inherits staff_id)
Represents managerial roles

## 🏟️ Facility

Stores sport facilities.

- facility_id (PK)
- facility_name
- requirement
- price

## 📅 Booking

Links customers to facilities.

- booking_id (PK)
- customer_id (FK)
- facility_id (FK)
- booking_date
- booking_time
- status

## 🛍️ Merchandise

Stores items sold by the centre.

- merchandise_id (PK)
- merchandise_name
- price

## 📦 Orders

Stores customer orders.

- order_id (PK)
- customer_id (FK)
- staff_id (FK)

## 🔄 OrderMerch

Resolves many-to-many relationship between Orders and Merchandise.

- order_id (FK)
- merchandise_id (FK)

## 🔑 Key Relationships
- One Customer → Many Bookings
- One Facility → Many Bookings
- One Customer → Many Orders
- Many Orders ↔ Many Merchandise
- Staff → Manages Orders & Bookings
- Manager ⊂ Staff (Inheritance)

---

## 3NF Process:

Customer (customerID {PK}, fName, lName, email, phoneNo, DOB) 

Merch (merchID {PK}, merchName, desc, price,{ orderID {PK},  status,  orderDate qty}) 

Staff (staffID {PK}, fName, lName, role, salary, phoneNo, managedBy) 

Manager (managerID, fname, lname, phoneNo, department) 

Facility ({facilityID {PK}, facilityName, location,  desc, requirement, price { bookingID {PK}, status, bookingDate}}) 

 
UNF: 

 

Customer (customerID , fName, lName, email, phoneNo, DOB,{ bookingID , status, bookingDate facilityID ,facilityName, location,  desc, requirement, price},{ orderID {PK},  status,  orderDate ,qty{ merchID {PK}, merchName, desc, price}) 

Manager (managerID, fname, lname, phoneNo, department, { staffID , fName, lName, role, salary, phoneNo,}) 

 

1nf 

 

Customer(customerID{PK} , fName, lName, email, phoneNo, DOB) 

Booking (bookingID{PK}, status, bookingDate facilityID ,facilityName, location,  desc, requirement, price, customerID{fk}) 

Order(orderID {PK},  status,  orderDate ,qty, merchID {PK}, merchName, desc, price, customerID{fk}) 

Manager (managerID{PK}, fname, lname, phoneNo, department,) 

Staff ( staffID{PK} , fName, lName, role, salary, phoneNo, managerID{fk}) 

 

2nf 

 

Customer(customerID{PK} , fName, lName, email, phoneNo, DOB) 

Faxility (bookingID{PK}, status, bookingDate facilityID{PK},  ,facilityName, location,  desc, requirement, price, customerID{fk}) 

bookingID{PK}-> status, bookingDate facilityID ,facilityName, location,  desc, requirement, price, customerID{fk}) 

customerID{fk}-> x 

customerID{fk}, bookingID{PK}->x 

{PK}, (bookingID, status, bookingDate facilityID{PK },facilityName, location,  desc, requirement, price, customerID{fk}) 

 

 

Order(orderID {PK},  status,  orderDate ,qty, merchID {PK}, merchName, desc, price, customerID{fk}) 

 

orderID {PK},  ->},  status,  orderDate , customerID{fk} 

 

merchID {pk}-> merchName, desc, price 

orderID, merchID -> qty 

 

order( orderID{pk}, status,  orderDate , , customerID{fk}) 

merch (merchID {pk}-> merchName, desc, price) 

OrderMerch(orderID{pk}{fk}, merchID{pk},{fk}, qty) 

 

 

Manager (managerID{PK}, fname, lname, phoneNo, department,) 

Staff ( staffID{PK} , fName, lName, role, salary, phoneNo, managerID{fk}) 

 

3nf 

Customer(customerID{PK} , fName, lName, email, phoneNo, DOB) 

 

 

Booking (bookingID{PK}, status, bookingDate facilityID ,facilityName, location,  desc, requirement, price, customerID{fk}) 

 

 

Status ->x 

 

bookingDate-> x 

 

facilityID -> facilityID ,facilityName, location,  desc, requirement, price 

 

Booking (bookingID{PK}, customerID{fk} status, bookingDate, facilityID{fk}) 

Facility(facilityID ,facilityName, location,  desc, requirement, price) 

order( orderID, status,  orderDate ,qty, customerID{fk}) 

status->x 

orderDate -> x 

qty->x 

 

merch (merchID {pk},merchName, desc, price) 

merchName->x, 

desc->x 

price->x 

 

order(orderID{pk}, status,  orderDate , , customerID{fk}) 

merch (merchID {pk}-> merchName, desc, price) 

OrderMerch(orderID{pk}{fk}, merchID{pk},{fk}, qty) 

 

Manager (managerID{PK}, fname, lname, phoneNo, department,) 

Staff ( staffID{PK} , fName, lName, role, salary, phoneNo, managerID{fk}) 

 
