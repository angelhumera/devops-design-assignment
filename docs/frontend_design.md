# Frontend (UI) Architecture Design

## Overview
For the frontend, I am using a React application. After building it, the output becomes simple static files. These files are stored in an S3 bucket and delivered to users through CloudFront. This setup is lightweight, highly available, and fits perfectly with the assignment requirement of a scalable UI design.

---

## How the UI Is Hosted
- The React build folder (HTML, CSS, JS) is uploaded to an S3 bucket.
- S3 hosts these files as static content.
- The bucket does not need any servers and scales automatically with traffic.

---

## How Users Reach the UI
- Users open the application using a domain.
- Route 53 (optional but commonly used) points the domain to CloudFront.
- CloudFront delivers the UI from the nearest edge location, making it load faster.

Flow:  
**User → Route 53 → CloudFront → S3**

---

## Scaling
- S3 automatically handles unlimited incoming requests.
- CloudFront serves cached copies, which reduces load on S3.
- This makes the UI highly scalable without any manual effort.

---

## Caching / CDN
- CloudFront stores and serves cached versions of static files.
- This improves speed and reduces cost.
- When a new UI version is uploaded, CloudFront cache can be invalidated.

---

## Availability
- S3 stores data across multiple Availability Zones by default.
- CloudFront uses globally distributed edge servers.
- This ensures the UI stays available even if one zone has issues.

---

## Security
- The S3 bucket stays private.
- CloudFront is the only service allowed to access S3.
- HTTPS is enabled using an SSL certificate.

---

## Deployment Steps
1. Build the React project using `npm run build`
2. Upload the build folder to the S3 bucket
3. Invalidate the CloudFront cache
4. Updated UI becomes live immediately

---

## Why I chose this design
I picked this setup because it is easy to manage and works well for any frontend application.  
Since React builds into static files, hosting it on S3 and delivering it through CloudFront makes the application load fast and handle more users without extra work.  

This approach is simple, reliable, and fits well with the assignment's requirement of designing a scalable frontend.

