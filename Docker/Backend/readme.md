#### Edit context.xml file and add ip address of db-container

#### Create Docker Image
````
docker build -t tomcat .
````

#### Create Docker Container
````
docker run -itd --name tomcat-be -p 8080:8080 tomcat
````

#### You can verify using below URL
````
instance-piblic-ip:8080/student
````
