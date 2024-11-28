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

```sql
CALL GetMaxQuantity('Deluxe');
```
#### ManageBooking()
```sql
DELIMITER //

CREATE PROCEDURE ManageBooking(IN booking_id INT, IN new_status VARCHAR(20))
BEGIN
    UPDATE bookings
    SET status = new_status
    WHERE booking_id = booking_id;
END //

DELIMITER ;
```
#### UpdateBooking()

```sql
DELIMITER //

CREATE PROCEDURE UpdateBooking(IN booking_id INT, IN new_check_in DATE, IN new_check_out DATE)
BEGIN
    UPDATE bookings
    SET check_in_date = new_check_in, check_out_date = new_check_out
    WHERE booking_id = booking_id;
END //

DELIMITER ;
```
#### AddBooking()
```sql
DELIMITER //

CREATE PROCEDURE AddBooking(IN customer_id INT, IN room_id INT, IN booking_date DATE, IN check_in DATE, IN check_out DATE)
BEGIN
    INSERT INTO bookings (customer_id, room_id, booking_date, check_in_date, check_out_date, status)
    VALUES (customer_id, room_id, booking_date, check_in, check_out, 'Booked');
END //

DELIMITER ;
```
#### CancelBooking()
```sql
DELIMITER //

CREATE PROCEDURE CancelBooking(IN booking_id INT)
BEGIN
    UPDATE bookings
    SET status = 'Cancelled'
    WHERE booking_id = booking_id;
END //

DELIMITER ;

```
## Tableau Charts


