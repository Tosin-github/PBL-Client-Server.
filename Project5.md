# Implement a Client Server Architecture using MySQL Database Management System (DBMS)

### How I deliver the project 5 end to end.

Create and Lunch two Ubuntu EC2 instance
Name it Server A and Server B
Update the system before starting

### The project is to demonstrate the basic client server architecture using Structure Query Language to create user database on mysql-server and able to communicate with mysql-client using local ip addreses to connect from mysql-client use TCP PORT 3306

# On server terminal

#sudo apt update -y

#sudo ap upgrade -y

#sudo apt install mysql-server

#sudo systemctl enable status


# On client terminal

#sudo apt update -y

#sudo apt upgrade -y

#sudo apt install mysql-client

#sudo systemctl enable mysql

# From the documentation
On mysql client Linux Server install MySQL Client software.
By default, both of your EC2 virtual servers are located in the same local virtual network, so they can communicate to each other using local IP addresses. Use mysql server's local IP address to connect from mysql client. MySQL server uses TCP port 3306 by default, so you will have to open it by creating a new entry in ‘Inbound rules’ in ‘mysql server’ Security Groups. For extra security, do not allow all IP addresses to reach your ‘mysql server’ - allow access only to the specific local IP address of your ‘mysql client’.

#Use mysql server private IP address to connect from mysql client. so, in otherwords

#go to security group add a new rule at mysql-client 

#type command 'ip address show'on mysql-server terminal

<img width="550" alt="sa" src="https://user-images.githubusercontent.com/79447751/119175035-40ff4f80-ba61-11eb-8c6d-d1499886ba8b.PNG">

#copy the server private ip address

#past mysql-server private ip in mysql-client

#Type: MYSQL/Aurora

#Protocol: TCP

#Source:past server ip and save the new rules bound

<img width="722" alt="cl" src="https://user-images.githubusercontent.com/79447751/119173873-c124b580-ba5f-11eb-9367-4791eb57dd67.PNG">


#follow thesame step on mysql-server environment.

#past mysql-client private ip in mysql-server

#Type: MYSQL/Aurora

#Protocol: TCP

#Source: past client ip and save the new rules bound

<img width="706" alt="cll" src="https://user-images.githubusercontent.com/79447751/119200292-8aad6180-ba84-11eb-9acb-cc466301da49.PNG">



# According to the documentation.

#On server terminal we need to run security script for smooth connectivity

#Run 'sudo mysql_secure_installation' It look like this

<img width="477" alt="zzz" src="https://user-images.githubusercontent.com/79447751/119177801-bddff880-ba64-11eb-97e2-12ce8246c57e.PNG">

#Run 'sudo mysql -u root -p'  to login in order to create users and create a databases, before we can query our databases.

##mysql# CREATE USER 'remote_user'@'%' IDENTIFIED WITH mysql_native_password BY 'password';

##mysql# CREATE DATABASE Tosin_db;

##mysql# GRANT ALL on Tosin_db.* To 'remote_user'@'%' WITH GRANT OPTION;

##mysql# FLUSH PRIVILEGES;

#<img width="152" alt="z" src="https://user-images.githubusercontent.com/79447751/119203034-0a89fa80-ba8a-11eb-874b-1055f4ab7167.PNG">

#<img width="295" alt="zzzzzz" src="https://user-images.githubusercontent.com/79447751/119203237-7cfada80-ba8a-11eb-858f-705be303a555.PNG">

##mysql# exit


#Run this command 'sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf' to change the bind address from (127.0.0.1 to 0.0.0.0)

#<img width="516" alt="xxxx" src="https://user-images.githubusercontent.com/79447751/119193144-18834f80-ba79-11eb-8a31-3b4f5c37deab.PNG">

#After changing bind address, then run the command 'sudo systemctl restart mysql' to save the changes and restart mysql-server.

# According to the documentation:

#From mysql client Linux Server connect remotely to mysql server Database Engine without using SSH. You must use the mysql utility to perform this action.
 Check that you have successfully connected to a remote MySQL server and can perform SQL queries:



#from mysql-client terminal

#Run sudo mysql -u 'username' -h 'server ip address' -p

#Enter the password you created for mysql.Then enter to connect to mysql-server LIKE THIS

#<img width="437" alt="zz" src="https://user-images.githubusercontent.com/79447751/119196848-be858880-ba7e-11eb-9520-55a7600ec2a3.PNG">







