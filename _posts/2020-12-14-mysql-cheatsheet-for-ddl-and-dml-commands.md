---
layout: post
title: "MYSQL cheatsheet for DDL, DML"
tags: "MySQL, CheatSheet, commands, DDL, DML"
---
Sql cheatsheet for CREATE , ALTER , DROP , TRUNCATE , DELETE ,RENAME , INSERT , DELETE queries 


### Create a table
```sql
CREATE TABLE User(
	uid INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
	name VARCHAR (50) NOT NULL,
	email VARCHAR (50) NOT NULL UNIQUE,
	password VARCHAR(255) NOT NULL,
	active Bool DEFAULT false,
	pid INT,
	CONSTRAINT FOREIGN KEY(pid) REFERENCES Profile(pid) ON DELETE CASCADE  
);
```

### Alter a table
```sql
ALTER TABLE Profile ADD Lname VARCHAR(30) NOT NULL AFTER Fname ;
ALTER TABLE Profile MODIFY contact VARCHAR(10) NOT NULL ;
ALTER TABLE Profile DROP COLUMN username;
ALTER TABLE Profile CHANGE COLUMN Fname first_name VARCHAR(30) FIRST ;
ALTER TABLE User ADD FOREIGN KEY(pid) REFERENCES Profile(pid);
```

### Drop a table
```sql
DROP TABLE table_name;
```

### Truncate a table (delete all entries)
```sql
TRUNCATE TABLE table_name;
```

### Rename a table
```sql
RENAME TABLE old_name TO new_name;
```

### Insert a row
```sql
INSERT INTO User(name,email,password) VALUES ("tom","riddle","tom.riddle@gmail.com");
```

### Update a row
```sql
UPDATE User SET name="Tom Riddle" WHERE email="tom.riddle@gmail.com";
```

### delete a row
```sql
DELETE FROM User WHERE name = "Tom Riddle";
```
