
# Database Design — 3-Tier Backend
This document explains the database part of my backend design.  

I am using **Amazon RDS** with **MySQL** as the database for the backend.  
The database is placed in a **private subnet** inside a VPC so it is not accessible from the internet.  
Only the **EC2 backend** can connect to it.  

Database credentials (username/password) are stored securely using **environment variables** or **AWS Secrets Manager**.  
Security groups ensure that only the EC2 instance can access the database.  

For reliability and scaling:  
- Multi-AZ deployment keeps the database available even if one availability zone fails.  
- Read replicas can be added later to handle more traffic.  
- Automatic backups are enabled so the database can be restored if needed.  

The backend EC2 instance connects to the database through the private subnet, and all communication is secure (SSL/TLS).  

**Flow:**  

EC2 (API) → Private Subnet → RDS MySQL Database
This setup keeps the database **secure, private, and ready to scale**, which matches the assignment requirements.
