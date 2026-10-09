# Week 1 - Day 1: Why Cloud + A Safe AWS Account

Live class: Saturday 10 Oct 2026, 7:00-9:00 PM IST
Exam focus: Domain 1 (Cloud Concepts), Domain 2 (Security), Domain 4 (Billing)
Exam tasks: 1.1 · 1.2 · 1.4 · 2.3 · 4.2

Pre-work: create your AWS account before the class (Lab 1 in [03-account-setup-console-tour.md](./03-account-setup-console-tour.md)) and keep an authenticator app ready on your phone.

## Practice Sequence

| Seq | Practice | File |
|---:|---|---|
| 01 | Why cloud and the problems it solves | [01-cloud-foundations.md](./01-cloud-foundations.md) |
| 02 | Six pillars, certifications and careers | [02-well-architected-and-careers.md](./02-well-architected-and-careers.md) |
| 03 | Create your account and tour the Console | [03-account-setup-console-tour.md](./03-account-setup-console-tour.md) |
| 04 | Root MFA and budget alert | [04-account-security-lab.md](./04-account-security-lab.md) |

PDF guide: [Day 1 Learner Guide](../pdf/Day01_Learner_Guide.pdf)

## By The End Of Today
- You can explain five problems the cloud solves and the six advantages of cloud computing.
- You can explain high availability, elasticity and agility, and basic cloud economics (fixed vs variable cost, BYOL, rightsizing).
- You know IaaS, PaaS and SaaS, and the six Well-Architected pillars.
- You know the CLF-C02 exam format.
- You can sign in, switch Regions and find your Free Tier or credits page.
- Your root user has MFA and you have a budget alert.
- You can name tasks only the root user can do, and tell Budgets, Cost Explorer and Pricing Calculator apart.

## Today's Deliverables
- Screenshot of Console Home with the Region visible (account ID hidden)
- Screenshot showing root MFA assigned (no QR, no codes)
- Screenshot of the budget list
- Account security checklist ticked in `notes.md`
- Career path notes in `notes.md` (exam details, job skills) from [02-well-architected-and-careers.md](./02-well-architected-and-careers.md)
- Day 1 LinkedIn post: see [10-linkedin-post.md](../10-linkedin-post.md)

## Self-Check: Exam-Style Questions
Answer first, then open the answer.

**1. A startup wants to avoid buying servers upfront and pay only for what it uses. Which cloud benefit is this?**

A. Economies of scale · B. Trade fixed expense for variable expense · C. Go global in minutes · D. High availability

<details><summary>Answer</summary>

**B.** Paying only for usage instead of buying upfront is trading fixed (capital) expense for variable expense.

</details>

**2. An app adds servers during a sale and removes them afterwards, automatically. What is this called?**

A. Agility · B. Elasticity · C. Durability · D. Rightsizing

<details><summary>Answer</summary>

**B. Elasticity**: resources grow and shrink with demand.

</details>

**3. Which Well-Architected pillar focuses on recovering quickly from failures?**

A. Operational Excellence · B. Performance Efficiency · C. Reliability · D. Security

<details><summary>Answer</summary>

**C. Reliability.**

</details>

**4. Which TWO actions best protect the root user? (Choose two.)**

A. Turn on MFA · B. Create root access keys for the CLI · C. Use an IAM user or role for daily work · D. Share the root password with your team

<details><summary>Answer</summary>

**A and C.** Never create root access keys and never share root credentials.

</details>

**5. Which task can ONLY the root user perform?**

A. Launch an EC2 instance · B. Create an S3 bucket · C. Close the AWS account · D. Create an IAM group

<details><summary>Answer</summary>

**C. Close the AWS account.**

</details>

**6. You want an email when monthly spend crosses USD 5. Which service?**

A. AWS Cost Explorer · B. AWS Budgets · C. AWS Pricing Calculator · D. AWS Artifact

<details><summary>Answer</summary>

**B. AWS Budgets.** It alerts you; it does not stop spending.

</details>

<div align="center">

[Week 1](../README.md) | [Day 2](../day-02/README.md)

</div>
