# Day 1 - Cloud Foundations

Goal: understand what the cloud is and which real problems it solves.

Exam tasks: 1.1 (benefits of the AWS Cloud), 1.4 (cloud economics), 3.1 (deployment models)

## Before You Start
Write answers in your own words before reading:
1. What is cloud computing? -->
2. Why would a company use cloud instead of its own servers? -->
3. Name one service you already use that runs on the cloud. -->

## The Story - Sale Night On A Shopping App
Think of **Flipkart Big Billion Days**, the **Amazon Great Indian Festival** or a **Myntra sale**. When the sale opens, people all over India open the app at the same moment. They search, add to cart and pay with **PhonePe** or **Google Pay**. A week later the rush is gone.

Now imagine **you** run an app like that. These are teaching numbers, not real company figures:

| When | Shoppers on the app | Servers you need |
|---|---|---|
| Normal day | A few thousand | 2 |
| Sale opens | Lakhs at once | 20 |
| A week later | A few thousand again | 2 |

**With your own servers:** you buy 20 servers for the sale, wait weeks for them to arrive, and pay for all 20 all year. For 50 weeks, 18 of them sit idle.

**With the cloud:** you add servers when the sale opens, remove them when it ends, and pay only for the hours you used them.

### Walk through one night - Amazon Great Indian Festival
You have been waiting for a phone deal. Follow your own steps and see what the app has to do at each one:

| Your step | What the app must do | Cloud word |
|---|---|---|
| 11:59 PM - you and lakhs of others open the app and keep refreshing | Handle a sudden rush without slowing down | Scalability, elasticity |
| 12:00 AM - the deal opens, you tap **Add to Cart** | Keep your cart even if one server fails | High availability |
| You pay with **PhonePe** or **Google Pay** | Never lose the order or the payment record | Reliability |
| You open **My Orders** | Show your orders and address only to you | Security |
| A week later the sale ends | Remove the extra servers and stop paying for them | Cost (pay for what you use) |

The same thing happens in **Flipkart Big Billion Days** and the **Myntra** sale.

These five steps are the five problems the cloud solves (next section). We describe only what you see as a user, not how these companies build their systems.

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

| Word | Meaning | Real-app example |
|---|---|---|
| High availability | The app keeps running when one part fails | The Amazon app still opens on sale night if one data centre has a problem |
| Elasticity | Resources grow **and shrink** automatically with demand | 2 servers normally, 20 when the sale opens, back to 2 after |
| Scalability | The system can handle more load by adding resources | Ready for more shoppers as the app grows every year |
| Agility | Try new things fast and cheaply | Try a new "Buy Now" button for one week, remove it if nobody uses it |

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

## Practice - Explore The Official AWS Pages
Practice in this order:

1. Open [What is cloud computing?](https://aws.amazon.com/what-is-cloud-computing/). Find the section on benefits.
2. Open [Types of cloud computing](https://aws.amazon.com/types-of-cloud-computing/). Find IaaS, PaaS and SaaS.
3. Open [AWS customer stories](https://aws.amazon.com/solutions/case-studies/). Filter by one industry you like (for example Education, Media or Financial Services).
4. Open one story. Read the headline and the results.

Add to your `notes.md`:

```text
Cloud in one line (my words):
One benefit I found on the AWS page:
Customer story I read (company + one result it mentions):
```

Expected result: three short lines in your notes, written in your own words.

## Official Links
| Topic | Link |
|---|---|
| What is cloud computing | https://aws.amazon.com/what-is-cloud-computing/ |
| Types of cloud computing (IaaS, PaaS, SaaS) | https://aws.amazon.com/types-of-cloud-computing/ |
| Six advantages of cloud computing | https://docs.aws.amazon.com/whitepapers/latest/aws-overview/six-advantages-of-cloud-computing.html |
| AWS customer stories | https://aws.amazon.com/solutions/case-studies/ |
| AWS Pricing overview | https://aws.amazon.com/pricing/ |

