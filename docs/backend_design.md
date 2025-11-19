# Backend (API) Architecture Design

## Where the API Runs
The backend API runs on a single **EC2 instance**.  
I chose EC2 because it is simple to set up and easy to understand for a basic backend design.

---

## How Traffic Reaches the Backend
Users or the frontend send requests to the EC2 public IP or domain.  
A security group allows only required ports (for example: port 80 or 443).

Flow:  
User → EC2 (Python API)

*I kept this part simple because EC2 itself can receive traffic.*

---

## Horizontal Scaling
If more users come, I can launch more EC2 instances and put them behind a load balancer.  
For now, I am using a **single EC2**, but the design can scale later by adding more servers.

---

## Secret Management
Database username and password are stored using **environment variables** on the EC2 instance.  
Only the EC2 instance can access these values.

---

## API → Database Communication
The EC2 instance connects to the database using the private endpoint inside the VPC.  
A database security group allows access only from the EC2 instance.

---

## Why I chose this design
This is a simple backend setup.  
EC2 is easy to understand, easy to deploy, and fits well for learning and basic projects.  
This also matches the assignment requirement of choosing one backend option.

