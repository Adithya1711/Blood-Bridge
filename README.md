# Blood-Bridge

## DB Setup
CREATE DATABASE bloodbridge;

USE bloodbridge;


CREATE USER 'DBAdmin'@'localhost' IDENTIFIED BY 'bloodbridge';

GRANT SELECT, INSERT, UPDATE, DELETE ON bloodbridge.* TO 'DBAdmin'@'localhost';

FLUSH PRIVILEGES;


CREATE TABLE register (
         id INT AUTO_INCREMENT PRIMARY KEY,
         fullname VARCHAR(255) NOT NULL,
         email VARCHAR(255) NOT NULL UNIQUE,
         password VARCHAR(255) NOT NULL,
         blood_type VARCHAR(10)
     );

CREATE TABLE request (
         id INT AUTO_INCREMENT PRIMARY KEY,
         requester_id INT NOT NULL,
         location VARCHAR(255) NOT NULL,
         blood_type VARCHAR(10) NOT NULL,
         urgency VARCHAR(50),
         date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
         status VARCHAR(50) DEFAULT 'pending',
         FOREIGN KEY (requester_id) REFERENCES register(id) ON DELETE CASCADE
     );


