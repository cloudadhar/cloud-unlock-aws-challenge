# Day 1 - Cloud Foundations

Goal: understand what the cloud is and which real problems it solves.

Exam tasks: 1.1 (benefits of the AWS Cloud), 1.4 (cloud economics), 3.1 (deployment models)

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

## Four Words The Exam Loves

| Word | Meaning | Fest example |
|---|---|---|
| High availability | The app keeps running when one part fails | Site stays up if one data centre has a problem |
| Elasticity | Resources grow **and shrink** automatically with demand | 2 servers normally, 20 on registration day, back to 2 |
| Scalability | The system can handle more load by adding resources | Ready to grow when the fest gets bigger every year |
| Agility | Try new things fast and cheaply | Launch a test feature in minutes, delete it if it fails |

Global reach is a benefit too: deploy close to users anywhere in minutes.

## Cloud Economics

| Idea | On-premises | AWS Cloud |
|---|---|---|
| Fixed vs variable cost | Big upfront spend (CapEx) on servers, buildings, power, cooling, staff | Pay for what you use (OpEx) |
| Hidden on-prem costs | Hardware refresh, electricity, cooling, floor space, security guards, data centre staff | Included in the service price |
| Economies of scale | Your small volume, your price | AWS buys at huge volume and passes savings on |
| Rightsizing | Hard: you already bought the server | Pick the right size, change it any time |
| Automation | Manual setup, slow, error-prone | Scripts and IaC: faster, repeatable, fewer mistakes |
| Licensing | You own licences | **BYOL** (bring your own licence) or **licence included** in the price |

Exam pointer:
- "Reduce upfront cost" or "trade capital expense for variable expense" = cloud economics.
- "Resources match demand automatically" = elasticity.
- "Already own Windows or Oracle licences" = BYOL.
- "Instance is too big for the workload" = rightsizing.

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
