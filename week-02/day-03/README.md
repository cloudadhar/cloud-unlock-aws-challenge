# Week 2 - Day 3: Ways To Access AWS, AWS CLI In CloudShell + Shared Responsibility

Live class: Saturday (date TBA), 7:00-9:00 PM IST
Exam focus: Domain 2 (Security and Compliance), Domain 3 (Technology)
Exam tasks: 2.1 · 2.2 · 3.1 · 3.2

Before class: root MFA, budget alert, `AdminGroup` and the IAM user `Cloud-Unlock` from [Week 1](../../week-01/README.md) are done. Sign in as `Cloud-Unlock`, not root.

Regions, Availability Zones and edge locations were taught on Day 1. Today we revise them in 5 minutes and then use them.

## Practice Sequence

| Seq | Practice | File |
|---:|---|---|
| 01 | Revise Regions, AZs, edge locations · 4 ways to access AWS · AWS CLI in CloudShell · Health Dashboard | [01-cloudshell-and-global-infrastructure.md](./01-cloudshell-and-global-infrastructure.md) |
| 02 | Shared responsibility model and compliance (AWS Artifact) | [02-shared-responsibility.md](./02-shared-responsibility.md) |

**Live class:** keep [practical-steps.md](./practical-steps.md) open and tick each step with the trainer.

Reference PDF (services, key ideas, official links): [Day 3 Reference Guide](../pdf/Day03_Reference_Guide.pdf). The steps are in the files above.

## By The End Of Today
- You can explain Regions, Availability Zones and edge locations, how to choose a Region, and when to use more than one.
- You know the four ways to access AWS, what `aws configure` needs, and ran AWS CLI commands in CloudShell (IAM lists, an S3 bucket).
- You know what AWS secures, what you secure, and what is shared.
- You know where to find AWS compliance reports (AWS Artifact).

## Today's Deliverables
- Screenshot of the Region list and Mumbai AZ table (account ID hidden)
- Four-line Region choice for the shopping app
- One line on what the Health Dashboard showed for Mumbai
- One AWS Artifact report name and who might ask for it
- Your 12 shared responsibility card-sort answers in `notes.md`
- LinkedIn post with `#CloudUnlock`

## Self-Check: Exam-Style Questions
Answer first, then open the answer.

**1. A company must keep customer data inside India. What should it do first?**

A. Use CloudFront · B. Choose an AWS Region in India · C. Use multiple AZs · D. Use AWS Artifact

<details><summary>Answer</summary>

**B.** Data residency and compliance decide the Region.

</details>

**2. How do you make an application highly available within one Region?**

A. Deploy across multiple Availability Zones · B. Use one large EC2 instance · C. Use edge locations only · D. Use AWS Budgets

<details><summary>Answer</summary>

**A.** AZs do not share a single point of failure.

</details>

**3. Which option lets a team create the same setup again and again in many accounts?**

A. AWS Management Console · B. Infrastructure as Code (AWS CloudFormation) · C. AWS Health Dashboard · D. AWS Artifact

<details><summary>Answer</summary>

**B.** Repeatable deployments = IaC.

</details>

**4. Under the shared responsibility model, who patches the guest operating system on an EC2 instance?**

A. AWS · B. The customer · C. Both equally · D. The AWS Partner Network

<details><summary>Answer</summary>

**B. The customer.**

</details>

**5. Which is a SHARED control?**

A. Physical security of data centres · B. Patch management · C. Deciding which Region stores your data · D. Replacing failed disks

<details><summary>Answer</summary>

**B. Patch management**: AWS patches the infrastructure, you patch your guest OS and apps.

</details>

**6. An auditor asks for AWS ISO and SOC reports. Where do you get them?**

A. AWS Trusted Advisor · B. AWS Artifact · C. AWS CloudTrail · D. AWS Health Dashboard

<details><summary>Answer</summary>

**B. AWS Artifact.**

</details>

<div align="center">

[Week 2](../README.md) | [Week 1](../../week-01/README.md)

</div>
