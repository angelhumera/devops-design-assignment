# Frontend (UI) Architecture Design

## Overview  
The frontend (React/Angular/Vue) is deployed using a fully serverless and highly available architecture on AWS using S3 and CloudFront.

---

## Components

### ✔ Route 53
- Points domain (eg:www.example.com)to CloudFront
- Global DNS service

### ✔ CloudFront (CDN)
- Caches static assets globally
- Reduces latency for users
- Protects S3 using Origin Access Control (OAC)

### ✔ AWS WAF
- Protects against OWASP Top-10 attacks
- Rate limiting + IP blocking

### ✔ S3 Static Hosting
- UI files (HTML, JS, CSS) stored in S3 bucket
- Bucket is fully private
- Only CloudFront can access it

---

## Scaling
- S3 is automatically scalable
- CloudFront has global edge locations
- No servers = infinite scaling

---

## Security
- HTTPS everywhere using ACM certificate
- WAF on CloudFront
- S3 bucket is private
- IAM role-based access control

---

## Deployment Flow
1. Developer pushes code  
2. Build system creates UI artifacts  
3. Upload to S3  
4. CloudFront cache invalidated  

This gives zero-downtime frontend updates.

