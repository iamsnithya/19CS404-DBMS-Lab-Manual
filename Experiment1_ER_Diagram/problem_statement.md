# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
<img width="737" height="376" alt="image" src="https://github.com/user-attachments/assets/6cfd28ad-3548-46a1-afe5-963122eb9e74" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|Members |Member_ID (PK), Name, Contact, Membership_Type|Enrolls in programs, makes payments|
|Programs        |Program_ID (PK), Type, Duration, Fees                    |Conducted by trainers       |
|Trainers        |Trainer_ID (PK), Name, Specialization, Contact                    |Conduct programs       |
|Enrollments        |Enrollment_ID (PK), Member_ID (FK), Program_ID (FK), Start_Date                    |M:N link between Members & Programs       |
|Program_Trainers        |Program_Trainer_ID (PK), Program_ID (FK), Trainer_ID (FK)                    |M:N link between Programs & Trainers       |
|Sessions        |Session_ID (PK), Program_ID (FK), Date, Time                    |Conducted under programs       |
|Attendance        |Attendance_ID (PK), Session_ID (FK), Member_ID (FK), Date, Status                    |Tracks member attendance per session       |
|Payments        |Payment_ID (PK), Member_ID (FK), Session_ID (FK), Amount, Payment_Type, Due_Date                    |Records payments made by members       |


### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|Member–Program              |M:N            |Partial               |Handled via Enrollments table       |
|Program–Trainer              |M:N             |Partial               |Handled via Program_Trainers table       |
|Member–Session              |M:N             |Partial               |Members attend multiple sessions       |
|Trainer–Session              |1:N            |Partial               |Trainer conducts sessions       |
|Session–Attendance              |1:N            |Total               |Each session has attendance       |
|Member–Payment              |1:N            |Total               |Member makes many payments       |

### Assumptions
- Each session is conducted under a specific program and may involve multiple members.

- A trainer can conduct multiple programs and sessions.

- Members can enroll in multiple programs and attend multiple sessions.

- Payments are made by members for programs or sessions.

- Attendance is recorded for each member per session.
 

---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
<img width="798" height="460" alt="image" src="https://github.com/user-attachments/assets/828f3a95-5b1f-40bf-be0b-66c125237a83" />

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|Member        |member_id (PK), name, contact_no, date                    |Registers for events, borrows books       |
|Book        |book_id (PK), title, author, category, purpose                    |Borrowed by members via loans       |
|Loan        |loan_id (PK), member_id (FK), book_id (FK), loan_date, due_date, return_date, fine                    |Records book borrow/return info       |
|Event        |event_id (PK), event_name, event_date                    |Registered by members, held in rooms       |
|Room        |room_id (PK), room_name, capacity                    |Hosts events, has speakers       |
|Speaker        |speaker_id (PK), name                    |Assigned to rooms for events       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|Member–Loan              |1:N            |Total               |Each member can have multiple loans       |
|Book–Loan              |1:N            |Total               |A book can be loaned multiple times       |
|Member–Event              |M:N            |Partial               |Members can register for multiple events       |
|Event–Room              |M:N            |Partial               |Events can occur in multiple rooms       |
|Room–Speaker              |M:N            |Partial               |Rooms can have multiple speakers       |
|Loan–Book              |1:N            |Total               |Each loan is linked to one book       |

### Assumptions
- Each loan record links one member to one book.

- A member can borrow multiple books but only one copy of the same book at a time.

- Events can occur in multiple rooms and may have multiple speakers.

- Speakers can present in multiple rooms or events.

- Members can register for multiple events.

- Fines are applied per loan record if the return date exceeds the due date.

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
<img width="932" height="467" alt="image" src="https://github.com/user-attachments/assets/1add826d-ff70-4f05-98e8-fe58c6273387" />

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|Customer        |customerID (PK), name, phone_no                    |Books reservations       |
|Reservation        |reservationID (PK), customerID (FK), tableID (FK), reservation_date_time                    |Manages table bookings       |
|Table        |tableID (PK), table_number, capacity, categoryID (FK)                    |Assigned to categories       |
|Category        |categoryID (PK), category_name                    |Groups tables       |
|Waiter        |waiterID (PK), name, phone_no                    |Serves orders       |
|Order        |orderID (PK), waiterID (FK), reservationID (FK), order_time                    |Linked to reservations and generates bills       |
|Bill        |billID (PK), orderID (FK), total_amount                    |Generated from orders       |
|Dish        |dishID (PK), name, price, categoryID (FK)                    |Belongs to a category       |


### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|Customer–Reservation              |1:N            |Total               |Each customer can make multiple reservations       |
|Reservation–Table              |M:N            |Partial               |Tables are assigned to reservations       |
|Table–Category              |1:N            |Total               |Each table belongs to one category       |
|Waiter–Order              |1:N            |Partial               |Waiters serve multiple orders       |
|Order–Bill              |1:1            |Total               |Each order produces one bill       |
|Bill–Dish              |M:N            |Partial               |A bill can include multiple dishes       |
|Dish–Category              |M:N            |Partial               |Dishes belong to a category type       |


### Assumptions
- Each customer can make multiple reservations but only one reservation per table at a time.

- A waiter can serve many orders but each order is served by one waiter.

- Every order generates exactly one bill.

- Each bill may contain multiple dishes.

- Tables are categorized (e.g., VIP, Regular, Outdoor).

- Dishes are grouped under menu categories.

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
