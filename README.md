# M5L1Assignments
Assignments for Database Fundamentals
## Assignment 1: BookHaven ERD
![BookHaven ERD (1)](https://github.com/kelseaconrad19/M5L1Assignments/assets/163567548/e507138e-7d91-4495-bf14-6a25fcfa0232)
### Analysis
#### 1st Normal Form
This ERD is in 1NF because it has no repeating groups and each field contains only atomic values. 
- For example, in the Customer's table, the **first_name** and **last_name** fields store only one name each.
- In addition, in the Books table, each book is represented by a unique **ISBN**. All other attributes have single values.

#### 2nd Normal Form
In this ERD, non-primary-key attributes are fully dependent on the primary key. 
- The Authors table is in 2NF as each non-primary-key attribute, such as **first_name** and **last_name**, is dependent on the primary key, **author_id**. There is no partial dependency on a subset of the primary key since **author_id** is a single-attribute primary key.
- The Orders table is also in 2NF. Every non-primary-key attribute is fully functionally dependent on the **order_number**, which is the primary key. There are no composite primary keys, eliminating the chance of partial dependency.

#### 3rd Normal Form
In this ERD, the attributes are dependent on the primary key and independent of each other.
- The Books table meets 3NF criteria as no non-primary key column, such as **title** or **publish_date**, depends on any other non-primary key column. The **author_id** serves as a foreign key linking to the Authors table, thereby preventing any transitive dependencies within the Books table.
- The Customers table adheres to 3NF as well. There are no fields that are dependent on other non-primary-key attributes; for example, **phone** is not dependent on **city** or **zip**.

## Assignment 2: AutoRent ERD
![AutoRent ERD](https://github.com/kelseaconrad19/M5L1Assignments/assets/163567548/2ee6c057-2efe-4d41-9228-b5a098b8228c)
### Analysis
#### New Vehicle Additions
When a new vehicle is added to the AutoRent fleet, a new entry is created in the Vehicle table. The vehicle_id is auto-incremented to ensure there is a unique identifier for each vehicle. Initially, there may not be a corresponding entry in the Rental_Agreement table since the vehicle is not yet rented out. The one-to-one relationship does not mandate the immediate creation of a rental agreement; it only restricts the number of agreements to one per vehicle when such an agreement is made.

#### Rental Agreement Updates
Updates to a rental agreement can occur in various scenarios, such as extending the rental period, updating renter details, or terminating the agreement early. The Rental_Agreement table accommodates updates to the start_date and end_date fields to reflect these changes. Since there is a foreign key constraint on vehicle_id, any update to the rental agreement must correspond to a vehicle existing in the Vehicle table. In the case of agreement termination, the corresponding entry in the Rental_Agreement table can be deleted, which would then allow for a new agreement to be created for that vehicle, maintaining the one-to-one relationship.
