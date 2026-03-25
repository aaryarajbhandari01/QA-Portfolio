## Overview

## 🧠 Database Schema Overview

### 🗂️ Core Tables

* **Customer** → Stores user details (name, email, age, phone)
* **Staff** → Employees managing operations
* **Manager** → Subset of staff with departments
* **Facility** → Sports facilities with pricing and requirements
* **Booking** → Tracks reservations (date, time, status)
* **Order** → Customer purchase records
* **OrderMerch** → Many-to-many relationship for orders and products
* **Merchandise** → Items available for sale

---

### 🔑 Key Relationships

* One **Customer → Many Bookings**
* One **Customer → Many Orders**
* One **Facility → Many Bookings**
* One **Order → Many Merchandise Items**
* One **Staff → Manages Bookings**
* One **Manager → Must exist in Staff (FK constraint)**

---

## 📂 SQL Query Categories

This repository is organised into structured SQL files:

| File Name                 | Description                                |
| ------------------------- | ------------------------------------------ |
| `SELECT_Queries.md`       | Basic data retrieval, filtering, ordering  |
| `JOIN_Queries.md`         | Multi-table relationships and joins        |
| `GROUP_BY_Queries.md`     | Aggregation and analytical queries         |
| `INSERT_UPDATE_DELETE.md` | Data manipulation and CRUD testing         |
| `Subquery.md`        | Advanced SQL logic                         |
| `Error_Scenarios.md`      | Negative testing and constraint validation |

---

## 🧪 QA Testing 

### ✅ Functional Testing

* Verifying correct query outputs
* Ensuring accurate joins and relationships

### ⚠️ Negative Testing

* Invalid inserts (NULL, wrong data types)
* Foreign key violations
* Duplicate primary keys

### 🔍 Data Validation

* Checking constraints (CHECK, NOT NULL, UNIQUE)
* Verifying aggregated results

### 🧩 Edge Case Testing

* Empty results (no bookings)
* Missing relationships
* Partial data scenarios


