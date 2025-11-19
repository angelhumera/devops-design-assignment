# DevOps Design Take-Home Assignment

This repository contains the design for a 3-tier backend system (UI, API, Database) with CI/CD workflow.
---
## Architecture Diagram
- Diagram created in Draw.io  
- Exported PDF: `diagram/architecture_design.pdf`  
- Draw.io diagram: architecture.drawio
## Design Overview

### 1. UI (Frontend)
- Hosted on S3 + CloudFront  
- Automatically scales with traffic  
- Uses CDN for caching and faster load  
- Available across multiple zones

### 2. API (Backend)
- Runs on EC2 (Python API)  
- Can scale horizontally behind ALB  
- Secrets (DB credentials/API keys) stored securely  
- Connects to database via private subnet

### 3. Database
- Amazon RDS MySQL in private subnet  
- Multi-AZ deployment for high availability  
- Read replicas and auto-scaling storage for load  
- Automatic backups enabled

### 4. CI/CD Pipeline
- Triggered on push to main or PR merge  
- Build: install dependencies, lint code  
- Test: unit + integration tests  
- Deploy: EC2 instances (rolling update if multiple)  
- Health check endpoint verifies deployment  
- Promotion: dev → stage → prod

---

## Flow Summary
User → UI → API → Database
Developer → GitHub → CI/CD → EC2 (API)
---
**Folder Structure**
backend_design.md
frontend_design.md
database_design.md
cicd_design.md
diagram/
This shows the overall design, scaling approach, and secure flow of the system.

