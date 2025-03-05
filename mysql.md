Here is your **MySQL Interview and Cheat Sheet** in **Markdown format**, with the interview questions at the top and the MySQL cheat sheet below.

---

# MySQL Interview Questions & Cheat Sheet

## 📝 MySQL Interview Questions

### 🔹 What is the default MySQL port?
- The default port for MySQL is **3306**.

### 🔹 What do DDL, DML, and DCL stand for?
- **DDL (Data Definition Language)**: Manages database schemas (e.g., `CREATE TABLE`).
- **DML (Data Manipulation Language)**: Deals with data handling (e.g., `SELECT`, `INSERT`).
- **DCL (Data Control Language)**: Controls access permissions (e.g., `GRANT`, `REVOKE`).

### 🔹 What are the types of joins in MySQL?
- **Inner Join**: Returns matching rows from both tables.
- **Left Join**: Returns all rows from the left table and matching ones from the right.
- **Right Join**: Returns all rows from the right table and matching ones from the left.
- **Full Join**: Returns all rows with matches in either table (not natively supported in MySQL).

### 🔹 What is a HEAP table?
- HEAP (Memory) tables store data in **RAM** for fast access.
- **Does not support** `TEXT`, `BLOB`, or `AUTO_INCREMENT`.

### 🔹 What are the different types of tables in MySQL?
- **MyISAM**: Default, sequential access, fast reads.
- **HEAP**: In-memory, but volatile.
- **InnoDB**: Supports transactions (`COMMIT`/`ROLLBACK`).
- **BDB**: Transaction support but slower than InnoDB.

### 🔹 What happens when a disk is full?
- Move `.frm` and `.idb` files to a soft link directory.

---

## 🛠 MySQL Cheat Sheet

### 🏗️ Initial Setup
```sql
mysql_secure_installation
```

### 🔗 Connecting to MySQL
```sh
mysql -h localhost -u root -p
```

### 🔑 Change Root Password
```sh
mysqladmin -u root -p password newpasswd
```

### 🗄️ Backup & Restore
**Backup all databases:**
```sh
mysqldump --all-databases --all-routines -u root -p > ~/fulldump.sql
mysqldump -u root -ptecmint rsyslog > rsyslog.sql  # Specific database
```

**Restore all databases:**
```sh
mysql -u root -p < ~/fulldump.sql
```

---

## 📌 Database Management

### Create a Database with UTF-8 Encoding
```sql
CREATE DATABASE mydb CHARACTER SET utf8 COLLATE utf8_general_ci;
```

### Grant Permissions to a User
```sql
GRANT ALL PRIVILEGES ON database.* TO 'user'@'localhost' IDENTIFIED BY 'password' WITH GRANT OPTION;
```

### Show Privileges for the Current User
```sql
SHOW GRANTS FOR CURRENT_USER();
SHOW GRANTS;
SHOW GRANTS FOR CURRENT_USER;
```

---

## 🔍 Querying Data

### Select All Data
```sql
SELECT * FROM table_name;
```

### Insert Data
```sql
INSERT INTO table_name (col1, col2) VALUES (15, col1 * 2);
```

### Update Data
```sql
UPDATE table_name SET col1 = "example";
```

### Delete Data
```sql
DELETE FROM table_name WHERE user = 'jcole';
```

---

## 📋 Managing Tables

### Show Databases & Tables
```sql
SHOW DATABASES;
SHOW TABLES;  -- After connecting to a database
```

### Connect to a Database
```sql
USE database_name;
```

### Show Fields of a Table
```sql
DESCRIBE table_name;
```

### Delete Tables & Databases
```sql
DROP TABLE table_name;
DROP DATABASE database_name;
```

### View Table Data
```sql
SELECT * FROM table_name;
SELECT column_name FROM table_name;
SELECT column1, column2 FROM table_name WHERE column_name = "value";
SELECT COUNT(*) FROM table_name;
```

---

## 📏 Performance Optimization

### View Database Size
```sql
SELECT table_schema AS "Database", 
ROUND(SUM(data_length + index_length) / 1024 / 1024, 2) AS "Size (MB)" 
FROM information_schema.TABLES 
GROUP BY table_schema;
```

### Optimize Query Cache
```sql
mysql -u root -p
SHOW VARIABLES LIKE 'query_cache_%';
```

Edit MySQL config file (`/etc/mysql/my.cnf`):
```ini
[mysqld]
query_cache_type=1
query_cache_size=12M
query_cache_limit=256K
```

Restart MySQL server:
```sh
sudo systemctl restart mysql
```

---

## 📂 MySQL File System
### What is a `.frm` File?
- `.frm` files store table **structure definitions** in MySQL.
- They have the **same name** as their associated table.

---

## 📚 Additional Cheat Sheet Items

### **Show Running Processes**
```sql
SHOW PROCESSLIST;
```

### **Kill a Running Query**
```sql
KILL thread_id;
```

### **List All Users**
```sql
SELECT user, host FROM mysql.user;
```

### **Change User Password**
```sql
ALTER USER 'username'@'host' IDENTIFIED BY 'newpassword';
```

### **Check Table for Errors**
```sql
CHECK TABLE table_name;
```

### **Repair a Corrupted Table**
```sql
REPAIR TABLE table_name;
```

### **Show Indexes of a Table**
```sql
SHOW INDEX FROM table_name;
```

---

## 🔗 Useful MySQL Resources
- [MySQL Documentation](https://dev.mysql.com/doc/)
- [MySQL Performance Tuning](https://dev.mysql.com/doc/refman/8.0/en/optimization.html)
- [MySQL Cheat Sheet](https://www.mysqltutorial.org/mysql-cheat-sheet.aspx)

---

This markdown file includes:
- **Interview Questions** at the top.
- **A comprehensive MySQL cheat sheet** with additional helpful commands.

