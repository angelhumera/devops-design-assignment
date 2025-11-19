# Database Design — 3-Tier Backend

This is the database part of my backend design.  

- I am using **Amazon RDS** with **MySQL** for the database.  
- The database is in a **private subnet** inside a VPC, so it is **not accessible from the internet**.  
- Only the **EC2 backend** can connect to it.  

For security:  
- Database credentials are stored safely (like environment variables or AWS Secrets Manager).  
- Security groups make sure only the backend EC2 can access the database.  

For scaling and reliability:  
- Multi-AZ deployment keeps it highly available.  
- Read replicas can be added if needed.  
- Automatic backups are turned on so data can be restored anytime.  

**How it connects to the backend:**  
The backend EC2 instance connects to the database through a private subnet in the VPC.  
Only the EC2 instance can access the database, and all communication is secure (SSL/TLS).  


