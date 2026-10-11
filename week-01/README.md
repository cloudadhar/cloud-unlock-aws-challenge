# Week 1 - Cloud Foundations + Account Security

CloudAdhar x AWS Student Builder Group at MIT ADT University
Live classes: Saturday 10 Oct and Sunday 11 Oct 2026, 7:00-9:00 PM IST
Exam focus: CLF-C02 Domain 1 (Cloud Concepts), Domain 2 (Security and Compliance), Domain 4 (Billing)
Main pillars: Security and Cost Optimization

This week is about basics. Before IAM, storage, or servers, first understand what the cloud is, get your AWS account ready, and lock it down.

## Start Here
Go step by step. Do not finish everything in one sitting.
- First understand these words: cloud, Region, Availability Zone, shared responsibility, root user.
- Create your account **before the Day 1 live class** (see below).
- Day 1: secure the root user with MFA and create an IAM admin user. Day 2: start with a budget alert and an IAM admin group, before you explore anything else.
- If the optional challenge feels hard, skip it for now.
- Submit whatever you complete with honest notes. Do not stay silent.

## Before Day 1 (Pre-work)
Create your AWS account before Saturday's live class: follow Lab 1 in [03-account-setup-console-tour.md](./day-01/03-account-setup-console-tour.md). Card verification and activation can take time. If you get stuck, join anyway; we will help live.

Keep ready: a phone with an authenticator app (Google Authenticator, Microsoft Authenticator or similar) for MFA.

## What You Should Know By The End Of The Week
- You can explain what AWS is and five problems it solves (scaling, cost, availability, security, reliability).
- You know the six advantages of cloud computing, basic cloud economics and the six Well-Architected pillars.
- You know the AWS certification path and common cloud roles.
- You can sign in, switch Regions and find your credits/Free Tier page.
- You know what Regions, Availability Zones and edge locations are.
- You can explain IAM users, groups, policies and roles, and you practised least privilege (allowed vs denied).
- Your root user has MFA, you have a budget alert, and you work as an IAM user in an admin group (not as root).

## Practice Sequence

| Seq | When | Practice | File |
|---:|---|---|---|
| 01 | Sat (Day 1) | Why cloud and the problems it solves | [01-cloud-foundations.md](./day-01/01-cloud-foundations.md) |
| 02 | Sat (Day 1) | Careers, certifications, opportunities and networking | [02-well-architected-and-careers.md](./day-01/02-well-architected-and-careers.md) |
| 03 | Sat (Day 1) | Create your account and tour the Console | [03-account-setup-console-tour.md](./day-01/03-account-setup-console-tour.md) |
| 04 | Sat + Sun | Root MFA + IAM admin user (Day 1) · budget + IAM group (Day 2) | [04-account-security-lab.md](./day-01/04-account-security-lab.md) |
| 05 | Sun (Day 2) | IAM basics: users, groups, policies, roles, least privilege | [05-iam-basics.md](./day-02/05-iam-basics.md) |
| 06 | Sun (Day 2) | IAM hands-on: read-only groups, allowed vs denied, custom policy, switch role | [06-iam-hands-on-lab.md](./day-02/06-iam-hands-on-lab.md) |
| 07 | Optional | Sale-day shopping app architecture and cost estimate challenge | [07-optional-challenge.md](./07-optional-challenge.md) |
| 08 | End of week | Clean up | [08-cleanup.md](./08-cleanup.md) |
| 09 | End of week | Submit your work | [09-submission-format.md](./09-submission-format.md) |
| 10 | End of week | LinkedIn post | [10-linkedin-post.md](./10-linkedin-post.md) |
| 11 | Before Week 2 | Revise for quiz | [11-quiz-prep.md](./11-quiz-prep.md) |

Day guides: [Day 1 (Sat)](./day-01/README.md) | [Day 2 (Sun)](./day-02/README.md)

Reference PDFs (services, key ideas, official links; steps are in the READMEs): [Day 1](./pdf/Day01_Reference_Guide.pdf) | [Day 2](./pdf/Day02_Reference_Guide.pdf)

## Minimum Submission For Week 1
- Root MFA proof (no QR code)
- Budget alert proof
- IAM user and IAM group proof (account ID hidden)
- One allowed and one `Access Denied` screenshot
- One short note on what you understood and where you got stuck
- LinkedIn post link

## Exam + Pillar Mapping

| Topic | Exam mapping | Pillar | Best practice |
|---|---|---|---|
| Benefits of cloud (Task 1.1) | Domain 1 | Cost Optimization | Pay for what you use |
| Cloud economics (Task 1.4) | Domain 1 | Cost Optimization | Rightsize, automate |
| Well-Architected pillars (Task 1.2) | Domain 1 | All six | Design with the six pillars |
| Regions and AZs (Task 3.2) | Domain 3 | Reliability | Use multiple AZs |
| Least privilege, IAM policies and roles (Task 2.3) | Domain 2 | Security | Grant only what is needed; roles instead of access keys |
| Root MFA (Task 2.3) | Domain 2 | Security | Protect the root user |
| Budgets (Task 4.2) | Domain 4 | Cost Optimization | Monitor cost from day one |
| IAM user and group (Task 2.3) | Domain 2 | Security | Do daily work as an IAM user; manage permissions with groups |

## Rules
Read [../RULES.md](../RULES.md). Never share access keys, MFA QR codes, OTPs, card details or your account ID.

<div align="center">

[Home](../README.md) | [Week 2](../week-02/)

</div>
