# 🚀 AWS EC2 + Elastic Load Balancer

> **A hands-on AWS project demonstrating traffic distribution, health checks, and high availability using EC2 and Elastic Load Balancer.**

---

## 📌 Project Overview

In this project, I designed and implemented an AWS architecture where an **Elastic Load Balancer (ELB)** distributes incoming user requests across multiple **Amazon EC2 instances**.

The architecture demonstrates how AWS can improve **availability, reliability, and scalability** by distributing traffic between healthy EC2 instances.

---

# 🏗️ Architecture

```text
                         🌐 USER
                            |
                            | Request
                            ↓
                ┌──────────────────────┐
                │  Elastic Load Balancer│
                │         (ELB)         │
                └──────────┬───────────┘
                           |
                    Health Check
                           |
                 ┌─────────┴─────────┐
                 ↓                   ↓
          ┌─────────────┐     ┌─────────────┐
          │    EC2-01   │     │    EC2-02   │
          │   Instance  │     │   Instance  │
          └──────┬──────┘     └──────┬──────┘
                 |                    |
                 └─────────┬──────────┘
                           |
                           ↓
                     User Response
