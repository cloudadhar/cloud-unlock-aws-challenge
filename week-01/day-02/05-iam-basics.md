# Day 2 - IAM And AWS Budgets: Key Ideas

Goal: understand how AWS decides who can do what.

Exam tasks: 2.3 (AWS access management), 4.2 (billing tools)

Remember this:

> Identity + Permissions = Access

## The Story
Think of your **college ERP**. A student sees only their own marks. Faculty can enter marks. The admin manages everything. Same app, different access. That is what IAM does for your AWS account.

## IAM In Simple Words

| IAM word | One line | College ERP example |
|---|---|---|
| **User** | One person with a login | You, with your student login |
| **Group** | A team of users with the same access | All faculty |
| **Policy** | JSON rules that allow or deny actions | "Faculty can edit marks" |
| **Role** | Temporary access for a task, no password | A visitor pass that expires |
| **Root user** | The sign-up email, full access | The college owner's master key |

Login access does not mean full access. **Policies decide what a user can do.**

- **Authentication** = proving who you are (sign in).
- **Authorization** = what you are allowed to do (policies).

## IAM Users
- A named identity for one person (or an application).
- Signs in to the Console with a password, and can have MFA.
- Example from Day 1: `Cloud-Unlock` is your daily admin user.

## IAM Groups
- A collection of users with common permissions.
- Attach the policy to the **group**, then add users to the group.
- A group cannot contain another group.

Examples we use today:

| Group | Policy | User | Can do | Cannot do |
|---|---|---|---|---|
| `AdminGroup` | `AdministratorAccess` | `Cloud-Unlock` | Everything (daily admin) | Root-only tasks |
| `S3ReadOnlyGroup` | `AmazonS3ReadOnlyAccess` | `Cloud-Unlock-S3` | View buckets and files | Create or delete |
| `EC2ReadOnlyGroup` | `AmazonEC2ReadOnlyAccess` | `Cloud-Unlock-EC2` | View EC2 | Launch, stop, terminate |
| `BillingViewGroup` | `AWSBillingReadOnlyAccess` | `Cloud-Unlock-Billing` | View bills and costs | Manage S3 or EC2 |

Exam pointer: "manage permissions for many users" = **IAM groups**.

## IAM Policies
An IAM policy is a JSON document. It has three main words:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    { "Effect": "Allow", "Action": ["s3:Get*", "s3:List*"], "Resource": "*" }
  ]
}
```

| Word | Meaning |
|---|---|
| `Effect` | `Allow` or `Deny` |
| `Action` | What can be done, for example `s3:ListBucket` |
| `Resource` | On which resource, `*` means all |

Types:
- **AWS managed policy:** created and maintained by AWS, for example `AmazonS3ReadOnlyAccess`.
- **Customer managed policy:** created by you and reusable.
- **Inline policy:** attached directly to one user, group or role, and deleted with it.

Rule: an explicit **Deny** always wins over an Allow. If nothing allows an action, it is denied by default.

## IAM Roles
- A role gives **temporary** credentials. No password, no long-term keys.
- Used when:
  - an AWS service needs to call another AWS service (for example, an EC2 server reading S3);
  - a person switches into a role for a task.

Exam pointer: "an application on EC2 needs to access S3" = **IAM role**, not access keys in code.

## Least Privilege
Give only the permissions needed for the task.
- Needs to view S3 only → `AmazonS3ReadOnlyAccess`, not full access.
- Needs to view EC2 only → `AmazonEC2ReadOnlyAccess`, not `AdministratorAccess`.
- Finance needs to see the bill → `AWSBillingReadOnlyAccess`, not access to servers.
- A Myntra support agent can see an order but cannot delete the catalogue.

## Keeping Access Safe
- **MFA** on the root user and on every IAM user.
- **Access keys** are for the CLI or code. Never share them, never put them on GitHub. Never create them for root.
- **Password policy:** set a minimum length and require numbers and symbols.
- Do daily work as an IAM user. Use root only for root-only tasks.

## AWS Budgets And The Cost Tools

| Service | What it does | When you use it |
|---|---|---|
| **AWS Budgets** | Sends an alert when cost or usage crosses your limit | While you run things |
| **AWS Cost Explorer** | Shows past spend and a forecast | After you spend |
| **AWS Pricing Calculator** | Estimates cost before you build | Before you build |

Exam pointer: a budget **alerts**; it does **not** stop spending.

## Official Links
| Topic | Link |
|---|---|
| What is IAM | https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html |
| IAM best practices | https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html |
| IAM groups | https://docs.aws.amazon.com/IAM/latest/UserGuide/id_groups_create.html |
| Policies and permissions | https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html |
| IAM roles | https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html |
| AWS Budgets | https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-managing-costs.html |
| IAM roles for Amazon EC2 | https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html |
| Billing access for IAM users | https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/control-access-billing.html |
