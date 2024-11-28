# Database-Engineering-Capstone-Project
## Over View
This project implements a booking system with functionalities to manage customers, rooms, and bookings. It includes database creation, Python integration, Tableau connectivity for data visualization, and the implementation of SQL procedures for managing bookings. The project is designed for scalability and ease of use.
## ER Diagram
The system's Entity-Relationship (ER) diagram illustrates the relationships between the Customers, Rooms, and Bookings tables.

Relationships:
* Customers → Bookings: One-to-Many
* Rooms → Bookings: One-to-Many
![ER Diagram](https://github.com/user-attachments/assets/a30eedf2-1366-4867-90c4-4cdf93f4f33b)

## Stored Procedures
#### GetMaxQuantity()
 Fetch the maximum capacity of rooms for a given room type.
 ```sql
 DELIMITER //

CREATE PROCEDURE GetMaxQuantity(IN room_type VARCHAR(50))
BEGIN
    SELECT MAX(max_capacity) AS max_quantity
    FROM rooms
    WHERE room_type = room_type;
END //

DELIMITER ;
```
