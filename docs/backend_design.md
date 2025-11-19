# Backend (API) Architecture Design — EC2 + Python (Step by Step)

## 1️⃣ Where the API Runs
- The backend API runs on a **single EC2 instance**.  
- Python (Flask/FastAPI) is used to implement the API.  
- EC2 is chosen because it is simple to set up and easy to understand.  

---

## 2️⃣ How Traffic Reaches the Backend
- Users or the frontend send requests to the EC2 **public IP or domain**.  
- **Security groups** allow only required ports (HTTP 80 / HTTPS 443).  
- For scalability, an **Application Load Balancer (ALB)** can be added later.  

**Traffic Flow:**  

---

## 3️⃣ Horizontal Scaling
- Currently using a single EC2 instance.  
- To handle higher traffic:
  - Launch more EC2 instances
  - Add them to an **ALB**
  - Use **Auto Scaling Groups (ASG)** to automatically adjust instance count based on CPU/memory/load.

---

## 4️⃣ Secret Management
- Database credentials and API keys are stored as **environment variables** on EC2.  
- Only the EC2 instance can access them.  
- Best practice: Use **AWS Secrets Manager** in production.

---

## 5️⃣ API → Database Communication
- EC2 connects to the database via **private VPC endpoint**.  
- Database security group allows access only from the EC2 instance.  
- Communication is **encrypted (SSL/TLS)**.

---

## 6️⃣ Why This Design
- Simple, easy-to-understand 3-tier architecture.  
- Supports **future scaling** with ALB + ASG.  
- Ensures **secure backend-to-database communication**.  
