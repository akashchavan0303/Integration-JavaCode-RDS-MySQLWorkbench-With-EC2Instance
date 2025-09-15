🔹 Step 1: Create RDS (MySQL)
=
1.Go to AWS Console → RDS → Create Database.

2.Engine = MySQL (or Aurora MySQL).

3.Deployment = Standard.

4.Templates = Free tier (if testing).

5.Set:
      * DB name = javacode-rds-project
      
      *Master username = admin
      
      *Password = Admin123456
      
      *Connectivity:
      
6.VPC = same VPC where your EC2 will be launched.

     *Public Access = No (best practice, keep private). 
     *Security group: create/select one (we’ll edit later).
     *Create database → wait for Available.

👉 Note the RDS endpoint (example: javacode-rds-project.cb0y2csmwusj.ap-south-1.rds.amazonaws.com).
<img width="1911" height="920" alt="image" src="https://github.com/user-attachments/assets/5e055d67-31dc-41a0-a6d6-7dfdb141b206" />
<img width="1910" height="918" alt="image" src="https://github.com/user-attachments/assets/c005fb14-bbfc-470c-b7c4-35ae527ec678" />


🔹 Step 2: Create EC2 Instance
=
1.Go to EC2 → Launch Instance.

2.AMI = Amazon Linux 2023 (or Ubuntu 22.04).

3.Instance type = t2.micro (free tier).

4.Key pair = choose/create (for SSH).

5.Network settings:

VPC = same as RDS.

Subnet = same or peered subnet.

Security group = allow:

   * 22 (SSH) from your IP.
   * 8080 (Tomcat) or 80 (HTTP) for web app.

 6.Launch instance.

👉 Note the Public IP (to access via browser).
<img width="1905" height="910" alt="image" src="https://github.com/user-attachments/assets/18fb1052-22b9-4415-b08d-837dd4f0919a" />


🔹 Step 3: Security Group Configuration
=
RDS Security Group:

Inbound rule → MySQL/Aurora (3306).
Source = EC2’s security group (not 0.0.0.0/0 ❌).
<img width="1906" height="908" alt="image" src="https://github.com/user-attachments/assets/593c1c88-c946-40dd-9622-15b5803f9ad9" />

EC2 Security Group:

Inbound → SSH (22) from your IP.
Inbound → HTTP (80) or Tomcat (8080) from anywhere.
<img width="1907" height="911" alt="image" src="https://github.com/user-attachments/assets/e9b54ab5-5970-4b9c-aff9-638d994ed88d" />


🔹 Step 4: Connect EC2 to RDS
=

1.SSH into EC2:

ssh -i mykey.pem ec2-user@13.200.251.169
Install MySQL client (for testing):

2.sudo dnf install mariadb105 -y

   (Ubuntu: sudo apt-get install -y mysql-client)

3.Test connection:

mysql -h javacode-rds-project.cb0y2csmwusj.ap-south-1.rds.amazonaws.com -u admin -p
If it connects, ✅ EC2 → RDS network is working.


🔹 Step 5: Create Database & Table in RDS
=
  Inside MySQL shell:
  

Database Creation code:-

create database storage;

Database using code:-

use storage;

Table creation code:-

CREATE TABLE users (

id INT AUTO_INCREMENT PRIMARY KEY,

name VARCHAR(100) NOT NULL,

address VARCHAR(200),

contact VARCHAR(15)

);


Table Data:-

INSERT INTO users (name, address, contact) VALUES

('Alice Johnson', '123 Main St, Springfield', '555-1234'),

('Bob Smith', '456 Oak Ave, Rivertown', '555-5678'),
<img width="1918" height="1010" alt="Screenshot 2025-09-15 131826" src="https://github.com/user-attachments/assets/de74b254-e153-4424-aaa4-da79a53d1dd0" />

🔹 Step 6: Install Java on EC2
=
Java installation code:-

sudo yum install java-17-amazon-corretto-devel -y


MySQL installation code:-

sudo dnf install mariadb105 -y


jdbc driver:-

wget https://github.com/awslabs/aws-mysql-jdbc/releases/download/1.1.15/aws-mysql-jdbc-1.1.15.jar


nano UserDatabaseApp.java

🔹 Step 7: Deploy Your App Compile java file:-
=

javac -cp .:aws-mysql-jdbc-1.1.15.jar UserDatabaseApp.java

Run java file:
=

java -cp .:aws-mysql-jdbc-1.1.15.jar UserDatabaseApp

<img width="1907" height="915" alt="Screenshot 2025-09-15 133015" src="https://github.com/user-attachments/assets/fab09363-8048-449d-ab0d-2bf3b0b61f56" />

<img width="1918" height="1010" alt="Screenshot 2025-09-15 131826" src="https://github.com/user-attachments/assets/40d81ad1-e924-4f0f-a5ce-a8e3fcf0b0fd" />






                 


     

