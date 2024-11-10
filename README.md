# Blood-Bridge

<details id=1>
<summary><h2>DB Setup</h2></summary>
         
```mysql
CREATE DATABASE bloodbridge;

USE bloodbridge;
```

```mysql
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
```

Optional

```mysql
CREATE USER 'DBAdmin'@'localhost' IDENTIFIED BY 'bloodbridge';

GRANT SELECT, INSERT, UPDATE, DELETE ON bloodbridge.* TO 'DBAdmin'@'localhost';

FLUSH PRIVILEGES;
```
</details>



<details id=2>
<summary><h2>EC2 Commands</h2></summary>
         
```bash
sudo yum update -y

sudo yum install python3 python3-pip git -y

sudo pip3 install virtualenv

python3 -m venv venv

source venv/bin/activate

pip install flask mysql-connector-python
```

```bash
git clone (git repo link)

cd (repo name)
```

Do the necessary configuration and then run the app

```bash
python3 app.py
```

</details>

## Use the application

- Go to your EC2 instance and then copy the public_IP
- Open a browser tab and then search for the following public_IP:5000
- Boom and here you have the web application
