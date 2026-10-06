# Day 1 - Cloud Foundations

Goal: understand what the cloud is and which real problems it solves.

## Before You Start
Write answers in your own words before reading:
1. What is cloud computing? -->
2. Why would a company use cloud instead of its own servers? -->
3. Name one service you already use that runs on the cloud. -->

## The Story
Your college fest website gets 50 visitors a day for 360 days, then 50,000 on registration day. With your own servers you buy for the peak, wait weeks, and pay all year. With cloud you rent what you need in minutes and pay only for what you use.

## Five Problems The Cloud Solves

| Problem | Without cloud | With AWS | Service (later) |
|---|---|---|---|
| Scaling (autoscaling) | Buy for the peak | Capacity grows and shrinks with traffic | EC2 Auto Scaling, Elastic Load Balancing |
| Cost | Large upfront spend | Pay for what you use | Budgets, Cost Explorer |
| Availability | One data centre fails, site down | Spread across Availability Zones | Multi-AZ, Route 53, CloudFront |
| Security | You secure everything alone | Shared responsibility | IAM, KMS, Security Groups |
| Reliability | Manual backups | Automated backups and replication | S3, RDS, AWS Backup |

## Six Advantages Of Cloud Computing
1. Trade fixed expense for variable expense.
2. Benefit from massive economies of scale.
3. Stop guessing capacity.
4. Increase speed and agility.
5. Stop spending money running and maintaining data centres.
6. Go global in minutes.

## Service Models
- **IaaS**: you manage OS and apps (Amazon EC2).
- **PaaS**: you manage app and data; the platform is managed (Elastic Beanstalk, RDS).
- **SaaS**: you just use it (Gmail, Microsoft 365).

## Deployment Models
- Cloud, on-premises (private cloud), and hybrid (both together).

Exam pointer:
- Pay-as-you-go and no upfront cost point to cloud benefits.
- Own data centre plus AWS together means hybrid.
- You manage the OS means IaaS.
