** MERN Food Delivery App Deployment on AWS ECS**

A complete production-style deployment of a MERN Stack Food Delivery Application using Docker, Amazon ECS with self managed ec2 instances (EC2 Launch Type), Amazon ECR, Application Load Balancer, VPC ,IAM ROLES and MongoDB Atlas.

**📌 Project Overview**

This project demonstrates how to deploy a containerized MERN application on AWS using ECS with EC2 launch type.

**Tech Stack**
Frontend

React.js

Backend
Node.js
Express.js
Database
MongoDB Atlas
DevOps & Cloud
Docker
Amazon ECS
Amazon EC2
Amazon ECR
Application Load Balancer (ALB)
IAM
VPC
CloudWatch
🏗️ Architecture
User
  ↓
Application Load Balancer (ALB)
  ↓
ECS Services
  ↓
Docker Containers running on EC2
  ↓
MongoDB Atlas
📂 Project Structure
project/
│
├── frontend/
│   ├── Dockerfile
│   └── React Application
│
├── backend/
│   ├── Dockerfile
│   └── Node.js API
│
└── docker-compose.yml
🐳** Dockerization**
Frontend Dockerfile

Backend Dockerfile

🚀 Deployment Steps
Step 1 — Build Docker Images
Frontend
docker build -t frontend-app .
Backend
docker build -t backend-node .
Step 2 — Create Amazon ECR Repositories
Created two repositories:
frontend-app
backend-node
Step 3 — Login to ECR
aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin <ACCOUNT_ID>.dkr.ecr.ap-south-1.amazonaws.com
Step 4 — Tag Docker Images
Frontend
docker tag frontend-app:latest <ACCOUNT_ID>.dkr.ecr.ap-south-1.amazonaws.com/frontend-app
Backend
docker tag backend-node:latest <ACCOUNT_ID>.dkr.ecr.ap-south-1.amazonaws.com/backend-node
Step 5 — Push Images to ECR
Frontend
docker push <ACCOUNT_ID>.dkr.ecr.ap-south-1.amazonaws.com/frontend-app
Backend
docker push <ACCOUNT_ID>.dkr.ecr.ap-south-1.amazonaws.com/backend-node
☁️ ECS Cluster Setup
Created ECS Cluster:
Configuration	Value
Cluster Name	
Launch Type	EC2
Region	ap-south-1
🖥️ EC2 Container Instances
ECS automatically registered EC2 instances
Containers deployed on ECS container instances
Auto Scaling Group attached
📦 ECS Task Definitions
Created separate task definitions for:
Frontend Container
Backend Container
🌐 ECS Services
Created ECS services to manage containers.
Responsibilities
Maintain desired task count
Restart failed tasks
Register tasks with ALB
Handle deployments
⚖️ Application Load Balancer
Created internet-facing ALB.
Configuration
Setting	Value
Name	ec2-alb
Type	Application
Scheme	Internet-facing
🎯 Target Group
Created target group:
Setting	Value
Name	ec2-tg
Protocol	HTTP
Port	80
Target Type	Instance

Health checks configured successfully.

*** MongoDB Atlas Configuration****

Connected backend to MongoDB Atlas.

**Application successfully deployed using ALB DNS:**

http://ec2-alb-1436319519.ap-south-1.elb.amazonaws.com
