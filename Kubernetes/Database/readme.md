## Create Database In RDS 

**Go To RDS**
- Created Database
- Standard create
- choose template as Free tier
- DB name – database-1
- Username – admin
- Password – Passwd123$
- VPC – VPC-3-tier
- Connect to Instance -> choose database instance
- create security group
**Create database**

  ### $$\color{orange} \textbf {Now SSH  into Database  Server}$$

![database-instance](https://github.com/abhipraydhoble/Project-3-tier-Student-App/assets/122669982/8159a278-d612-441e-93da-d581428cdd3a)

**steps to install db on amazon linux**
````
yum update
yum install mariadb105-server-y
````
**steps to install db on ubuntu server**
````
sudo apt update -y
sudo  apt install mariadb-server -y
````
````
systemctl start mariadb
````
````
systemctl enable mariadb
````
### $\color{orange} \textbf{Log \ in \ into \ database}$

![login into database](https://github.com/abhipraydhoble/Project-3-tier-Student-App/assets/122669982/ba0c082a-060f-48f9-8520-83c906337251)

````
mysql -h rds-endpoint   -u admin -pPasswd123$
````
Note: replace rds-endpoint with actual endpoint value

````
show databases;
````
````
create database  studentapp;
````
````
use studentapp;
````

### $\color{blue} \textbf{Run \ this \ query \ to \ create \ table:}$
````
 CREATE TABLE if not exists students(student_id INT NOT NULL AUTO_INCREMENT,  
	student_name VARCHAR(100) NOT NULL,  
	student_addr VARCHAR(100) NOT NULL,   
	student_age VARCHAR(3) NOT NULL,      
	student_qual VARCHAR(20) NOT NULL,     
	student_percent VARCHAR(10) NOT NULL,   
	student_year_passed VARCHAR(10) NOT NULL,  
	PRIMARY KEY (student_id)  
);
````
````
show tables;
````
Logout from database:
````
exit
````
<img width="1872" height="672" alt="image" src="https://github.com/user-attachments/assets/d4c024cb-accc-4011-b3ec-cfa386aed41f" />
<img width="1682" height="183" alt="image" src="https://github.com/user-attachments/assets/a11a0a72-59be-4329-b096-e746aba61550" />
<img width="1687" height="537" alt="image" src="https://github.com/user-attachments/assets/43afb8f9-5796-4661-a4b1-c59e9dfbc3d6" />
<img width="1686" height="287" alt="image" src="https://github.com/user-attachments/assets/d07a20da-1b63-4c63-a7da-029fe2ba0042" />
<img width="1687" height="132" alt="image" src="https://github.com/user-attachments/assets/b9438759-68a5-4e16-935f-e1804e520a64" />






