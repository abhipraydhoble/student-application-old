#### Edit index.html file and add backend URL 

#### Create Docker Image
````
docker build -t apache .
````

#### Create Docker COntainer
````
docker run -itd --name apache-fe -p 80:80 apache
````
#### Go to browser add public ip of instance you will see following UI

![image](https://github.com/user-attachments/assets/d22298f1-ce24-4c8e-b918-05e2758a5f4b)

#### Click on ***Enter to Student Application*** it will redirect you to backend page
 
![image](https://github.com/user-attachments/assets/0be68578-184b-4e74-bf2a-7cedcfa76058)

#### Student Data is saved into Database
![image](https://github.com/user-attachments/assets/1a9f90d1-042b-4fb1-88e9-337087768287)


