# Full-Stack MEAN Application: Containerization & CI/CD Deployment

This repository contains a full-stack MEAN (MongoDB, Express, Angular, Node.js) application, fully containerized and deployed using a robust CI/CD pipeline. The project demonstrates modern DevOps practices, including automated builds, cloud infrastructure management, and reverse proxy configuration.

 ## Project Overview

The goal of this assignment was to take a MEAN stack codebase and transform it into a production-ready environment by:

    Containerizing all services for environment consistency.

    Automating the deployment lifecycle with a CI/CD pipeline.

    Securing and routing traffic via an NGINX reverse proxy on AWS.

## Implementation Details
### 1. Containerization & Orchestration

I utilized Docker to ensure the application runs identically across all environments.

    Dockerfiles: Created custom images for both the Angular frontend and Node.js backend using optimized base images (e.g., node:18).

    Docker Compose: Integrated the frontend, backend, and MongoDB into a single docker-compose.yaml file to manage multi-container orchestration, networking, and volume persistence for the database.

### 2. Infrastructure & Server Configuration

    Cloud Provider: Deployed on an AWS EC2 Ubuntu 24.04 instance.

    Reverse Proxy: Configured NGINX as a reverse proxy to handle incoming traffic on Port 80. It efficiently routes requests to the frontend and backend services while masking internal port structures.

### 3. CI/CD Pipeline (Jenkins)

To achieve continuous deployment, I set up a Jenkins pipeline triggered by GitHub Webhooks:

    Poll/Trigger: Jenkins detects a new commit to the main branch.

    Build: Automatically builds updated Docker images.

    Registry: Pushes the latest images to Docker Hub.

    Deploy: Automatically pulls the new images on the AWS server and restarts the containers using Docker Compose, ensuring zero-to-minimal downtime.

<img width="1843" height="960" alt="UI" src="https://github.com/user-attachments/assets/a810675a-60be-43ef-9483-7916fa2d7ac6" />
<img width="1843" height="960" alt="UI-2" src="https://github.com/user-attachments/assets/ebfa35aa-6278-4f37-8209-50d1d79794ab" />
<img width="1843" height="960" alt="UI-3" src="https://github.com/user-attachments/assets/dd109a66-20db-4663-af28-96ae4f9ed59a" />
<img width="1843" height="960" alt="Jenkins" src="https://github.com/user-attachments/assets/dbb7237b-3369-46d6-856d-66ccf963643a" />
<img width="1843" height="960" alt="Jenkins Config" src="https://github.com/user-attachments/assets/1443b117-9087-4721-9f05-2c3dce4212ab" />
<img width="1843" height="960" alt="Webhook" src="https://github.com/user-attachments/assets/e5c95e52-258c-4da6-acb3-c6325fb4138b" />
