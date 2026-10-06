# Week 1 - Cloud Foundations + Account Security

CloudAdhar x AWS Student Builder Group at MIT ADT University
Live classes: Saturday 10 Oct and Sunday 11 Oct 2026, 7:00-9:00 PM IST
Exam focus: CLF-C02 Domain 1 (Cloud Concepts), Domain 2 (Security and Compliance), Domain 4 (Billing)
Main pillars: Security and Cost Optimization

This week is about basics. Before IAM, storage, or servers, first understand what the cloud is, get your AWS account ready, and lock it down.

## Start Here
Go step by step. Do not finish everything in one sitting.
- First understand these words: cloud, Region, Availability Zone, shared responsibility, root user.
- Then create or prepare your account and tour the Console.
- Then secure the root user and set a budget alert.
- If the optional challenge feels hard, skip it for now.
- Submit whatever you complete with honest notes. Do not stay silent.

## What You Should Know By The End Of The Week
- You can explain what AWS is and five problems it solves (scaling, cost, availability, security, reliability).
- You know the six advantages of cloud computing and the six Well-Architected pillars.
- You know the AWS certification path and common cloud roles.
- You can sign in, switch Regions and find your credits/Free Tier page.
- You ran your first commands in CloudShell.
- You know what Regions, Availability Zones and edge locations are.
- You know what AWS secures and what you secure.
- Your root user has MFA and you have a budget alert.

## Practice Sequence

| Seq | When | Practice | File |
|---:|---|---|---|
| 01 | Sat (Day 1) | Why cloud and the problems it solves | [01-cloud-foundations.md](./01-cloud-foundations.md) |
| 02 | Sat (Day 1) | Six pillars, certifications and careers | [02-well-architected-and-careers.md](./02-well-architected-and-careers.md) |
| 03 | Sat (Day 1) | Create your account, tour the Console, use CloudShell | [03-account-setup-console-tour.md](./03-account-setup-console-tour.md) |
| 04 | Sun (Day 2) | Regions, AZs and edge locations | [04-global-infrastructure.md](./04-global-infrastructure.md) |
| 05 | Sun (Day 2) | Shared responsibility model | [05-shared-responsibility.md](./05-shared-responsibility.md) |
| 06 | Sun (Day 2) | Root MFA and budget alert | [06-account-security-lab.md](./06-account-security-lab.md) |
| 07 | Optional | Fest app architecture challenge | [07-optional-challenge.md](./07-optional-challenge.md) |
| 08 | End of week | Clean up | [08-cleanup.md](./08-cleanup.md) |
| 09 | End of week | Submit your work | [09-submission-format.md](./09-submission-format.md) |
| 10 | End of week | LinkedIn post | [10-linkedin-post.md](./10-linkedin-post.md) |
| 11 | Before Week 2 | Revise for quiz | [11-quiz-prep.md](./11-quiz-prep.md) |

PDF guides: [Day 1](./pdf/Day01_Learner_Guide.pdf) | [Day 2](./pdf/Day02_Learner_Guide.pdf)

## Minimum Submission For Week 1
- Root MFA proof (no QR code)
- Budget alert proof
- Region/AZ CLI output (account ID hidden)
- One short note on what you understood and where you got stuck
- LinkedIn post link

## Exam + Pillar Mapping

| Topic | Exam mapping | Pillar | Best practice |
|---|---|---|---|
| Benefits of cloud | Domain 1 | Cost Optimization | Pay for what you use |
| Well-Architected pillars | Domain 1 | All six | Design with the six pillars |
| Regions and AZs | Domain 3 / 1 | Reliability | Use multiple AZs |
| Shared responsibility | Domain 2 | Security | Know AWS vs customer duties |
| Root MFA | Domain 2 | Security | Protect the root user |
| Budgets | Domain 4 | Cost Optimization | Monitor cost from day one |

## Rules
Read [../RULES.md](../RULES.md). Never share access keys, MFA QR codes, OTPs, card details or your account ID.

<div align="center">

[Home](../README.md) | [Week 2](../week-02/)

</div>
