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
     <img width="1900" height="920" alt="image" src="https://github.com/user-attachments/assets/369effda-66a3-4c3d-8ecd-4f137c4175e3" />
     <img width="1875" height="918" alt="image" src="https://github.com/user-attachments/assets/f2e0de61-fa0f-4d64-b43a-578c35a113ac" />


     

