# AWS EC2 with Elastic Load Balancer

## Project Overview

This project demonstrates how an Elastic Load Balancer (ELB) distributes incoming user requests across multiple Amazon EC2 instances.

The Load Balancer receives the user request and forwards it to a healthy EC2 instance through a Target Group.

## Architecture

User
  |
  v
Elastic Load Balancer
  |
  v
Target Group
  |-----------|
  v           v
EC2-1       EC2-2
  |           |
  |-----------|
       |
       v
User Response

## AWS Services Used

- Amazon EC2
- Elastic Load Balancer
- Target Group
- Security Group

## User Request Flow

1. User sends a request to the Load Balancer.
2. Elastic Load Balancer receives the request.
3. Load Balancer checks the registered EC2 instances.
4. Target Group identifies healthy EC2 instances.
5. Request is forwarded to a healthy EC2 instance.
6. EC2 processes the request.
7. Response is returned to the user through the Load Balancer.

## Security Group

Security Groups control inbound and outbound traffic between the Load Balancer and EC2 instances.

Traffic Flow:

User → Load Balancer → EC2

## Key Learning

- EC2 instance configuration
- Elastic Load Balancer
- Target Groups
- Health Checks
- Security Groups
- User request and response flow
- Traffic distribution
- High Availability

## Project Components

AWS EC2 + ELB
│
├── Elastic Load Balancer
├── Target Group
├── EC2 Instance 1
├── EC2 Instance 2
└── Security Groups

## Author

Mohit Gadilohar

BSc Computer Science | Cloud & DevOps Enthusiast
