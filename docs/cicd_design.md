# CI/CD Pipeline Design — Backend API Design.
This is a CI/CD workflow for the backend API using GitHub Actions (or GitLab/Jenkins).
---
## How it works:

1. **Trigger Events**  
   - Pipeline starts when someone **pushes to the main branch** or merges a pull request.

2. **Build Stage**  
   - Install dependencies  
   - Check code style  
   - Prepare the code for deployment

3. **Testing**  
   - Run unit tests  
   - Run integration tests  
   - Only pass code moves forward

4. **Deployment**  
   - Deploy code to **EC2 backend**  
   - Pull latest code and restart API  
   - If multiple EC2 instances, deploy one by one (rolling update)

5. **Health Checks**  
   - Check a simple API endpoint (like `/health`)  
   - Make sure API is running before marking deployment successful

6. **Promotion**  
   - First deploy to **development**  
   - Then to **staging**  
   - Finally to **production**

**Flow:**  
  Developer → GitHub → CI (Build + Test) → CD (Dev → Stage → Prod) → API Live
---
This shows how code goes from development to live API safely and automatically.


