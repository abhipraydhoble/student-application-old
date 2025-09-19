#### Create Docker Image

````
docker build -t mysql .
````

#### Create Container

````
docker run -itd --name mysql-db -p 3306:3306 mysql
````
#### Copy Container IP and add to context.xml file in Backend folder

````
docker inspect <containerID>
````

![image](https://github.com/user-attachments/assets/49147a3d-d764-4b53-a73b-5be1be2b8980)

**Login to DB Container**
````
docker exec -it dac6  mariadb --user root -p1234
```` 
