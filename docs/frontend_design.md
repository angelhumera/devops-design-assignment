# Frontend (UI) Architecture Design

## Overview
The frontend is a **React-based Single Page Application (SPA)**. It is built into static files and deployed on AWS using S3 and delivered globally through CloudFront. This design meets all assignment requirements for scalability, routing, caching, and multi-AZ availability.

---

## Components Used

### 1. Amazon S3 (Static Hosting)
- Stores the built React files (HTML, CSS, JS, images)
- Automatically scalable and serverless
- No servers to maintain
- Highly durable storage

### 2. Amazon CloudFront (CDN)
- Delivers UI globally through edge locations
- Caches static assets for faster load times
- Reduces latency for users around the world
- Routes traffic to S3

### 3. Amazon Route 53 (DNS)
- Manages the application domain (e.g., **www.example.com**)
- Routes end-user traffic to CloudFront
- Highly available DNS service

---

## Traffic Flow
User → Route 53 → CloudFront → S3

---

## High Availability & Multi-AZ
- S3 is inherently multi-AZ (AWS stores data redundantly)
- CloudFront uses globally distributed edge locations
- This ensures zero downtime and automatic failover

---

## Scaling
- **S3 scales automatically** with unlimited upload/download capacity
- **CloudFront handles very high global traffic**
- No manual scaling is needed

---

## Caching
- CloudFront caches frequently accessed files (JS, CSS, images)
- Reduces S3 load
- Improves webpage speed
- Reduces overall cost

---

## Security
- S3 bucket remains private
- Only CloudFront can read the S3 bucket (Origin Access Control)
- HTTPS enabled using AWS Certificate Manager (ACM)
- Optional restriction: allow traffic only from CloudFront

---

## Deployment Process
1. Developer builds the React app (`npm run build`)
2. Build output folder is uploaded to S3
3. CloudFront cache is invalidated so users receive
