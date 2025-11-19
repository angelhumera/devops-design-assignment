# Database Architecture — Tier Backend System

This folder contains the database design for a simple 3-tier backend architecture.

---

## Database Overview
- **Database Service:** Amazon RDS (Relational Database Service)  
- **Database Engine:** MySQL (relational database, as mentioned in the assignment)  
- **Deployment:** Private subnet inside a VPC (not publicly accessible)  

---

## point
1. **Secure Access**
   - Only the backend EC2 instance can connect to the database.  
   - Security groups restrict access.  
   - Credentials stored securely using **AWS Secrets Manager**.

2. **High Availability & Scalability**
   - Multi-AZ deployment for high availability.  
   - Optional read replicas for scaling read-heavy workloads.  
   - Storage auto-scaling enabled.

3. **Backup & Recovery**
   - Automatic backups enabled.  
   - Point-in-time recovery supported.

4. **Communication with API**
   - EC2 backend connects via **private VPC endpoint**.  
   - All communication is encrypted (SSL/TLS).

**Flow Diagram :**
---
## Purpose
- Ensures **secure, scalable, and highly available database** for the backend.  
- Matches assignment requirements: relational database, secure communication, scalability, and AWS best practices.


