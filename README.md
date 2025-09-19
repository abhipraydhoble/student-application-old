# $${\color{red} \textbf{Project}: \textbf{Student}  \ \textbf{App}}$$


## 1. Create Security Group and add following ports
- 80 = HTTP
- 22 = SSH 
- 8080 = Tomcat 
- 3306 = Mysql / Mariadb



## 2. Launch ec2 instance

<img width="1920" height="712" alt="image" src="https://github.com/user-attachments/assets/07bd79aa-85cd-44af-ba14-2b479bb911f0" />



## 3. Go to RDS Service and create DB instance

<img width="1920" height="716" alt="image" src="https://github.com/user-attachments/assets/385b90ab-165a-4a98-9b42-eb3635db3551" />

## 4. SSH into ec2 instnce

**Download mariadb-server using  below command**

````
yum install mariadb105-server -y
systemctl start mariadb    
systemctl enable mariadb  
systemctl status mariadb
````

## log in into DB-instance

````
mysql -h "rds-endpoint"   -u admin -pPasswd123$
````
Note: replace rds-endpoint with actual endpoint value

<img width="1918" height="792" alt="image" src="https://github.com/user-attachments/assets/7bf8db48-9e71-4341-b5a1-61706543e65c" />

## Create database 
````
create database  studentapp;
````
```sql
show databases;
```
````
use studentapp;
````
 
## Create table

```sql
 CREATE TABLE if not exists students(student_id INT NOT NULL AUTO_INCREMENT,  
	student_name VARCHAR(100) NOT NULL,  
	student_addr VARCHAR(100) NOT NULL,   
	student_age VARCHAR(3) NOT NULL,      
	student_qual VARCHAR(20) NOT NULL,     
	student_percent VARCHAR(10) NOT NULL,   
	student_year_passed VARCHAR(10) NOT NULL,  
	PRIMARY KEY (student_id)  
);
```
## Logout from database:
```sql
 exit
```

## 5. Set up Application

### Install Java
````
yum install java-1.8* -y 
````

### Install tomcat

![tomcat](https://github.com/abhipraydhoble/Project-Student-App/assets/122669982/8e622609-b7df-4f26-b8e3-e787e5e16c95)

````
wget  https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.108/bin/apache-tomcat-9.0.108.zip
````
````
unzip apache-tomcat-9.0.108.zip
````
````
cd  apache-tomcat-9.0.108
````

### go to webapps directory and paste this link to download student.war
````
curl -O https://s3-us-west-2.amazonaws.com/studentapi-cit/student.war
````
### go to lib directory and paste this link
````
curl -O https://s3-us-west-2.amazonaws.com/studentapi-cit/mysql-connector.jar 
````

## Modify context.xml file to setup database connection with database

```
cd /conf
```
````
vim context.xml
````

````
 <Resource name="jdbc/TestDB" auth="Container" type="javax.sql.DataSource"
               maxTotal="100" maxIdle="30" maxWaitMillis="10000"
               username="USERNAME" password="PASSWORD" driverClassName="com.mysql.jdbc.Driver"
               url="jdbc:mysql://DB-ENDPOINT:3306/DATABASE"/>

````
<img width="1901" height="387" alt="image" src="https://github.com/user-attachments/assets/130a5ba6-90f8-4883-b5ca-96568d324f7d" />

* Change  
1.Username  
2.Password   
3.DB-ENDPOINT  
4.DATABASE Name
  
### go to bin dir abd assign +x permission to catakina.sh
````
cd bin
````
````
chmod +x catalina.sh     
````
### Start Tomcat
````
sh catalina.sh start
````


## 6. go to browser and public ip:8080/student

<img width="1920" height="948" alt="image" src="https://github.com/user-attachments/assets/a1adae20-ec85-472d-9c93-153a7bb71ae0" />

<img width="1917" height="345" alt="image" src="https://github.com/user-attachments/assets/9a037325-a902-4d6f-976c-c4b371caa317" />



 


