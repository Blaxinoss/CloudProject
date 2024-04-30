# CloudProject
Docker-Composer project

After Downloading the files and putting them together on whatever destination you want 

open cmd and search for services.msc
once you opened your services.msc scroll down till you find mysql or mysql 80 and disable that service 

---------------------------------------------------------------------------------------------------------
after disabling your sql you will need to run docker-composer by the following steps :

1- open cmd 
2- go to the directory that contains the dockerfile , ex: cd desktop cd ProjectCloud
3- type the next command : docker-compose up --build 
4- once the command executed it will give you an error that the database don't exist don't worry don't close anything 
5- open mysql workbench and create a new connection with the following details :
 host name : 127.0.0.1
 port : 3306
 Username : abdullah
 then press okay and connect to that connection and enter the next password 
 123564

6- once you are in create a database called maybe and copy paste the next code inside it :

-- Create a database
SELECT 'Executing init.sql script...' AS 'Message';

CREATE DATABASE IF NOT EXISTS maybe;

-- Create a new user 'abdullah' with password '123564' and grant privileges on the 'maybe' database

CREATE USER 'abdullah'@'%' IDENTIFIED WITH mysql_native_password AS '123564';
GRANT ALL PRIVILEGES ON maybe.* TO 'abdullah'@'%';
FLUSH PRIVILEGES;

-- Use the created database
USE maybe;

-- Create a table for students
CREATE TABLE IF NOT EXISTS students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    age INT NOT NULL,
    cgpa DECIMAL(3, 2) NOT NULL,
    student_id VARCHAR(10) NOT NULL
);



SELECT 'init.sql script execution completed.' AS 'Message';

once this script done now you can back to the cmd and terminate it by pressin ctrl c then docker-compose down 
then run it again and it will connect successfully 

