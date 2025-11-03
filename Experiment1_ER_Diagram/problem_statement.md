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
<img width="807" height="515" alt="image" src="https://github.com/user-attachments/assets/de1682bd-8526-464e-b255-8dee603ad71b" />


### Entities and Attributes
1.Members
Name
Contact number
Address
2.Programs
Type
Duration
Fees
3.Trainers
Name
Specialization
Contact number
4.Payments
Amount
Payment Type
Due Date

### Relationships and Constraints
Members — Joins → Programs
A member joins one or more programs.
Programs — Conducts → Trainers
Trainers conduct programs.
Trainers — Duty → Payments
Payments are associated with trainers’ duties.



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
<img width="821" height="468" alt="image" src="https://github.com/user-attachments/assets/51166605-e14e-4295-ae1c-77355de24f60" />


### Entities and Attributes

1.MEMBER
memb_id
memb_name
contact no.
date
2.LOAN
loan_date
due_date
return_date
fine
memb_id
book_id
loan_id
3.BOOK
Title
Author
Category
book_id
4.Event
event_id
event_name
event_date
room_id
5.Speaker
speaker_id
name
6.Room
room_id
room_name
capacity
purpose


### Relationships and Constraints

Member ↔ Loan ↔ Book
A Member can borrow many Books (M:N, resolved via Loan).
Each Loan relates one Member to one Book.
Member ↔ Event
A Member can register for many Events.
An Event can have many Members.
M:N → resolved via Event_Registration.
Room ↔ Speaker
A Room can have multiple Speakers.
Event ↔ Room
Each Event occurs in exactly one Room (1:N).

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

<img width="601" height="304" alt="image" src="https://github.com/user-attachments/assets/8656adc0-c3f2-4370-8b0a-e1441309b2db" />

### Entities and Attributes


Customer
* customerID
* Name
* Phone no
2. Reservation
* reservationID
* Reservation date and time
* customerID
3. Table
* tableID
* Table number
* Capacity
4. Category
* categoryID
* Category Name
5. Dish
* dishID
* Name
* Price
* categoryID
6. Order
* orderID
* Order time
* reservationID
* waiterID
7. Bill
* billID
* Total amount
* orderID
8. Waiter
* waiterID
* Name
* Phone no


### Relationships and Constraints

1. Customer ↔️ Reservation
One customer books many reservations.
Each reservation belongs to one customer.
1 : N
2. Reservation ↔️ Table
One reservation is assigned to one table.
A table can be assigned to many reservations (over time).
1 : N
3. Reservation ↔️ Order
One reservation generates one or many orders.
Each order belongs to exactly one reservation.
1 : N
4. Waiter ↔️ Order
One waiter serves many orders.
Each order is served by exactly one waiter.
1 : N
5. Order ↔️ Bill
Each order produces one bill.
Each bill is linked to only one order.
1 : 1
6. Bill ↔️ Dish
A bill contains many dishes.
Each dish can appear in many bills.
M : N
7. Dish ↔️ Category
Each dish belongs to one category.
A category can contain many dishes.
1 : N
## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
