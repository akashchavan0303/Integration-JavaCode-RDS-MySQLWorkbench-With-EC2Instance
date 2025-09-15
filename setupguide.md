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
                   
                 


     

