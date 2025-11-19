# DevOps Design Assignment

This repository contains the design documents and diagrams for a 3-tier backend system.

## Design Diagram
- See `diagram/architecture_design.pdf` for the full architecture.

## Backend
- API runs on EC2 with Python.
- Can scale horizontally with multiple EC2s behind an ALB.
- Secrets stored securely (environment variables / AWS Secrets Manager).
- EC2 communicates with database via private subnet.

## Frontend
- Simple UI hosted separately.
- Communicates with backend API via HTTPS.

## Database
- Amazon RDS MySQL in a private subnet.
- High availability with Multi-AZ.
- Read replicas and auto-scaling storage for load handling.
- Only EC2 can access the database.

## CI/CD Pipeline
- Triggered on push to main or PR merge.
- Build: install dependencies, lint code.
- Test: unit and integration tests.
- Deploy: update EC2 API instances (rolling if multiple instances).
- Health checks: simple endpoint check.
- Promotion: dev → stage → prod.
