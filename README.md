# 📊 AWS CloudWatch + SNS EC2 Monitoring

![AWS](https://img.shields.io/badge/AWS-CloudWatch-orange)
![SNS](https://img.shields.io/badge/AWS-SNS-red)
![EC2](https://img.shields.io/badge/AWS-EC2-orange)
![Linux](https://img.shields.io/badge/Linux-Linux-black)
![Monitoring](https://img.shields.io/badge/Monitoring-AWS-blue)
![Status](https://img.shields.io/badge/Status-Completed-success)

---

## 📌 Project Overview

This project demonstrates how to monitor an **Amazon EC2 instance**
using **Amazon CloudWatch** and send automated notifications using
**Amazon SNS (Simple Notification Service)**.

The objective of this project is to monitor the CPU utilization of
an EC2 instance and trigger an email notification when CPU usage
exceeds the configured threshold.

This project provides practical experience with:

- AWS EC2
- Amazon CloudWatch
- CloudWatch Metrics
- CloudWatch Alarms
- Amazon SNS
- Email Notifications
- CPU Monitoring
- Linux
- AWS CLI
- Monitoring and Alerting

---

# 🎯 Project Objectives

The main objectives of this project are:

1. Launch and configure an EC2 instance.
2. Monitor EC2 CPU utilization using CloudWatch.
3. Create a CloudWatch alarm.
4. Configure a CPU utilization threshold.
5. Create an SNS topic.
6. Subscribe an email address to the SNS topic.
7. Connect CloudWatch Alarm with SNS.
8. Generate CPU load for testing.
9. Receive an automated email notification.
10. Understand AWS monitoring and alerting.

---

# 🛠️ Technologies Used

| Technology | Purpose |
|------------|---------|
| AWS EC2 | Compute server |
| Amazon CloudWatch | Monitoring and metrics |
| CloudWatch Alarm | Detect high CPU utilization |
| Amazon SNS | Notification service |
| Email | Receive alert notifications |
| Linux | EC2 operating system |
| AWS CLI | AWS resource management |
| Web Browser | AWS Console and testing |

---

# 📋 Prerequisites

Before starting this project, you should have:

- AWS Account
- EC2 access
- CloudWatch access
- SNS access
- AWS CLI installed
- Basic Linux knowledge
- Basic AWS knowledge
- Valid email address
- Required IAM permissions
- Internet connection

---

# 🏗️ Project Architecture

The basic architecture of this project is:

```text
                  👤 DevOps Engineer
                         |
                         |
                   🌐 AWS Console
                         |
                         |
                    🖥️ Amazon EC2
                         |
                         |
                  CPU Utilization
                         |
                         ▼
                📊 Amazon CloudWatch
                         |
                         |
                  🚨 CloudWatch Alarm
                         |
                    CPU > 70%
                         |
                         ▼
                    🔔 Amazon SNS
                         |
                         |
                         ▼
                    📧 Email Alert
                         |
                         ▼
                  👤 DevOps Engineer
