# Week 1 - Day 2: Global Infrastructure + Shared Responsibility

Live class: Sunday 11 Oct 2026, 7:00-9:00 PM IST
Exam focus: Domain 2 (Security and Compliance), Domain 3 (Technology)
Exam tasks: 2.1 · 2.2 · 3.1 · 3.2

Before class: make sure root MFA and your budget alert from [Day 1](../day-01/04-account-security-lab.md) are done. If you got stuck, bring a screenshot and we will help.

## Practice Sequence

| Seq | Practice | File |
|---:|---|---|
| 05 | Regions, AZs, edge locations, ways to access AWS, CloudShell, Health Dashboard | [05-global-infrastructure.md](./05-global-infrastructure.md) |
| 06 | Shared responsibility model and compliance (AWS Artifact) | [06-shared-responsibility.md](./06-shared-responsibility.md) |

PDF guide: [Day 2 Learner Guide](../pdf/Day02_Learner_Guide.pdf)

## By The End Of Today
- You can explain Regions, Availability Zones and edge locations, how to choose a Region, and when to use more than one.
- You know the four ways to access AWS and ran your first commands in CloudShell.
- You know what AWS secures, what you secure, and what is shared.
- You know where to find AWS compliance reports (AWS Artifact).

## Today's Deliverables
- Screenshot of the Region list and Mumbai AZ table (account ID hidden)
- Four-line Region choice for the fest-registration site
- One line on what the Health Dashboard showed for Mumbai
- One AWS Artifact report name and who might ask for it
- Your 12 shared responsibility card-sort answers in `notes.md`
- Day 2 LinkedIn post: see [10-linkedin-post.md](../10-linkedin-post.md)

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

## After Day 2
1. Optional: [07-optional-challenge.md](../07-optional-challenge.md)
2. Clean up: [08-cleanup.md](../08-cleanup.md)
3. Submit: [09-submission-format.md](../09-submission-format.md)
4. Revise: [11-quiz-prep.md](../11-quiz-prep.md)

<div align="center">

[Day 1](../day-01/README.md) | [Week 1](../README.md)

</div>
