# Week 1 - Day 2: Budget Alert + IAM Users, Groups, Policies And Roles

Live class: Sunday 11 Oct 2026, 7:00-9:00 PM IST
Exam focus: Domain 2 (Security and Compliance), Domain 4 (Billing)
Exam tasks: 2.3 · 4.2

Before class: root MFA and the IAM user `Cloud-Unlock` from [Day 1](../day-01/04-account-security-lab.md) are done. If you got stuck, bring a screenshot and we will help.

Regions, Availability Zones and edge locations were taught on Day 1. The AWS CLI and shared responsibility come on [Day 3](../../week-02/day-03/README.md).

## Practice Sequence

| Seq | Practice | File |
|---:|---|---|
| 04 | Budget alert, `AdminGroup`, MFA on `Cloud-Unlock`, sign in as `Cloud-Unlock` | [04-account-security-lab.md](../day-01/04-account-security-lab.md) (Labs 2 and 4) |
| 05 | Key ideas: IAM users, groups, policies, roles, least privilege, Budgets | [05-iam-basics.md](./05-iam-basics.md) |
| 06 | IAM hands-on: S3, EC2 and billing read-only users, allowed vs denied, read a policy (switch role optional) | [06-iam-hands-on-lab.md](./06-iam-hands-on-lab.md) |

**Live class:** keep [practical-steps.md](./practical-steps.md) open and tick each step with the trainer.

Reference PDF (services, key ideas, official links): [Day 2 Reference Guide](../pdf/Day02_Reference_Guide.pdf). The steps are in the files above.

## By The End Of Today
- You have a budget alert and know that budgets alert, they do not stop spending.
- Your admin access comes from `AdminGroup`, your IAM user has MFA, and you work as `Cloud-Unlock` (not root).
- You can explain IAM users, groups, policies and roles in one line each.
- You can read a simple IAM policy: `Effect`, `Action`, `Resource`.
- You practised least privilege with three users (S3, EC2, billing): what each can and cannot do.
- You know when to use a role (temporary access; an app on EC2 uses a role, not access keys) and the three policy types.

## Today's Deliverables
- Screenshot of the budget list
- Screenshot of `AdminGroup` with `Cloud-Unlock` (account ID hidden)
- Screenshot of one allowed action and one `Access Denied`
- `notes.md`: one line per policy (S3, EC2, billing)
- Day 2 LinkedIn post with `#CloudUnlock`: see [10-linkedin-post.md](../10-linkedin-post.md)

## Self-Check: Exam-Style Questions
Answer first, then open the answer.

**1. 50 new interns need the same read-only access. What is the best way?**

A. Attach a policy to each user · B. Create an IAM group with the policy and add the users · C. Share one IAM user · D. Use the root user

<details><summary>Answer</summary>

**B.** Attach policies to groups, then add users to groups.

</details>

**2. An application running on EC2 needs to read files from S3. What should you use?**

A. Access keys written in the code · B. An IAM role attached to the EC2 instance · C. The root user's access keys · D. A shared IAM user password

<details><summary>Answer</summary>

**B. An IAM role.** Roles give temporary credentials; never put access keys in code.

</details>

**3. One policy allows an action and another policy explicitly denies it. What happens?**

A. Allowed · B. Denied · C. The newer policy wins · D. AWS asks the user

<details><summary>Answer</summary>

**B. Denied.** An explicit Deny always wins.

</details>

**4. Giving users only the permissions they need is called:**

A. Elasticity · B. Least privilege · C. High availability · D. Rightsizing

<details><summary>Answer</summary>

**B. Least privilege.**

</details>

**5. In which format are IAM policies written?**

A. YAML · B. XML · C. JSON · D. CSV

<details><summary>Answer</summary>

**C. JSON.**

</details>

**6. You want an email when your monthly AWS spend goes over USD 5. Which service?**

A. AWS Cost Explorer · B. AWS Budgets · C. AWS Pricing Calculator · D. AWS CloudTrail

<details><summary>Answer</summary>

**B. AWS Budgets.** It alerts you; it does not stop spending.

</details>

## After Day 2
1. Optional: [07-optional-challenge.md](../07-optional-challenge.md)
2. Clean up: [08-cleanup.md](../08-cleanup.md)
3. Submit: [09-submission-format.md](../09-submission-format.md)
4. Revise: [11-quiz-prep.md](../11-quiz-prep.md)

<div align="center">

[Day 1](../day-01/README.md) | [Week 1](../README.md) | [Day 3](../../week-02/day-03/README.md)

</div>
