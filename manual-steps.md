
# Student Application Setup Guide


---

## Requirements
- **Ports:** `8080`, `22`, `3306`
- **Applications/Commands:** `git`, `unzip`

---

## Database Setup (MySQL/MariaDB)

### Install MariaDB
```bash
# yum install mariadb105-server -y
# systemctl start mariadb
# systemctl enable mariadb
# mysql_secure_installation
````

* Default username: **root**
* Set a password for the root user.
  Example login:

```bash
mysql -u root -p1234
```

### Create Database & Table

```sql
-- Create Database
CREATE DATABASE studentapp;

-- Switch to database
USE studentapp;

-- Create Table
CREATE TABLE IF NOT EXISTS students (
    student_id INT NOT NULL AUTO_INCREMENT,
    student_name VARCHAR(100) NOT NULL,
    student_addr VARCHAR(100) NOT NULL,
    student_age VARCHAR(3) NOT NULL,
    student_qual VARCHAR(20) NOT NULL,
    student_percent VARCHAR(10) NOT NULL,
    student_year_passed VARCHAR(10) NOT NULL,
    PRIMARY KEY (student_id)
);
```

Exit MySQL:

```bash
exit
```

---

## Install Java

```bash
yum install java-1.8* -y
```

---

## Install Tomcat

1. **Download Tomcat (v8.5.93)**

```bash
wget https://dlcdn.apache.org/tomcat/tomcat-8/v8.5.93/bin/apache-tomcat-8.5.93.zip
```

2. **Unzip & Navigate**

```bash
unzip apache-tomcat-8.5.93.zip
cd apache-tomcat-8.5.93
```

3. **Make Scripts Executable**

```bash
cd bin
chmod +x *.sh
```

4. **Tomcat Start/Stop**

```bash
./catalina.sh start
./catalina.sh stop
```

---

## Setup Student Application

1. **Clone Repository**

```bash
yum install git -y
cd
git clone https://github.com/abhipraydhoble/Student_App-Project.git
```

2. **Stop Tomcat**

```bash
cd apache-tomcat-8.5.93/bin
./catalina.sh stop
```

3. **Copy Application Files**

```bash
cp Student_App-Project/student.war apache-tomcat-8.5.93/webapps/
cp Student_App-Project/mysql-connector.jar apache-tomcat-8.5.93/lib/
```

4. **Modify Tomcat `context.xml`**

```bash
cd apache-tomcat-8.5.93/conf
vim context.xml
```

Add the following at **line 21**:

```xml
<Resource name="jdbc/TestDB" auth="Container" type="javax.sql.DataSource"
          maxTotal="100" maxIdle="30" maxWaitMillis="10000"
          username="USERNAME" password="PASSWORD" driverClassName="com.mysql.jdbc.Driver"
          url="jdbc:mysql://DB-ENDPOINT:3306/DATABASE"/>
```

Replace:

* `USERNAME` → MySQL username (e.g., `root`)
* `PASSWORD` → MySQL password (e.g., `1234`)
* `DB-ENDPOINT` → Database host (e.g., `localhost`)
* `DATABASE` → Database name (e.g., `studentapp`)

5. **Start Tomcat**

```bash
cd apache-tomcat-8.5.93/bin
./catalina.sh start
```

---

## Access Application

* [http://localhost:8080/student](http://localhost:8080/student)
* `http://<SERVER-IP>:8080/student`

---

✅ Your **Student Application** should now be running!



Do you want me to also **add architecture flow diagram + troubleshooting steps** into this README so it looks more professional?
```
