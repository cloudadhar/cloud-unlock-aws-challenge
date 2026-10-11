# Day 2 - IAM Hands-On Lab

Today, practise least privilege with three users: one can only view S3, one can only view EC2, one can only view billing.

Exam tasks: 2.3 (AWS access management), 4.2 (billing access)

## Practice Rule

Create only read-only access in this lab. Do not give full access unless asked. Do Labs 2 and 4 of [04-account-security-lab.md](../day-01/04-account-security-lab.md) first (budget, billing access and `AdminGroup`), then work as `Cloud-Unlock`.

Practice in this order:

1. Create group.
2. Attach read-only policy to group.
3. Create user.
4. Add user to group.
5. Test allowed access.
6. Test denied access.

## Before You Start - Turn On IAM Billing Access (root, once)

IAM users cannot see billing by default, even with the right policy. Only the root user can switch this on.

1. Sign in as **root** → account name (top right) → **Account**.
2. Find **IAM user and role access to Billing information** → **Edit**.
3. Tick **Activate IAM Access** → **Update**.

Do this once. Then sign out of root and work as `Cloud-Unlock`.

## Lab 1 - S3 Read-Only Access

Create:

- Group: `S3ReadOnlyGroup`
- Policy: `AmazonS3ReadOnlyAccess`
- User: `Cloud-Unlock-S3`

Steps (as `Cloud-Unlock`):

1. **IAM → User groups → Create group** → `S3ReadOnlyGroup` → attach `AmazonS3ReadOnlyAccess` → **Create user group**.
2. **IAM → Users → Create user** → `Cloud-Unlock-S3` → tick **Provide user access to the AWS Management Console** → **Custom password** → **Next**.
3. Permissions options: **Add user to group** → tick `S3ReadOnlyGroup` → **Next** → **Create user**.

Test:

- Open a private or incognito window. Sign in with your alias sign-in URL as `Cloud-Unlock-S3`.
- Open **S3**. The bucket list opens (**allowed**).
- Click **Create bucket** and try to create one. It fails (**Access Denied**).

Access Denied is not a failure today. It proves IAM is working.

## Lab 2 - EC2 Read-Only Access

Create:

- Group: `EC2ReadOnlyGroup`
- Policy: `AmazonEC2ReadOnlyAccess`
- User: `Cloud-Unlock-EC2`

Test:

- Sign in as `Cloud-Unlock-EC2`.
- Confirm the user can open the **EC2** dashboard and view instances and security groups.
- Click **Launch instance**, keep the defaults and launch. It fails (**denied**). Nothing is created.

## Lab 3 - Billing Read-Only Access

Create:

- Group: `BillingViewGroup`
- Policy: `AWSBillingReadOnlyAccess`
- User: `Cloud-Unlock-Billing`

Test:

- Sign in as `Cloud-Unlock-Billing`.
- Open **Billing and Cost Management**. The bills and costs are visible (**allowed**).
- Open **S3** or **EC2**. You get errors or "not authorized" (**denied**).

If Billing shows "access denied", the root step in **Before You Start** was not done.

## Lab 4 - Read A Policy (JSON)

1. **IAM → Policies** → search `AmazonS3ReadOnlyAccess` → open it → **JSON** tab.
2. Find `Effect`, `Action` and `Resource`.
3. Open `AmazonEC2ReadOnlyAccess` and `AWSBillingReadOnlyAccess` the same way. Compare the `Action` lines.
4. Write one line per policy in `notes.md`: what does it allow?

## Lab 5 - Switch Role (Optional Homework)

The trainer shows this live. Try it at home if you want to see a role in action.

Create a role:

- Role: `TrainingReadOnlyRole`
- Trusted entity: **AWS account** → **This account**
- Policy: `ReadOnlyAccess`

1. **IAM → Roles → Create role** → **AWS account** → **This account** → **Next** → tick `ReadOnlyAccess` → **Next** → name `TrainingReadOnlyRole` → **Create role**.
2. As `Cloud-Unlock`: top right account menu → **Switch role**.
3. Account: your account alias. Role: `TrainingReadOnlyRole` → **Switch role**.
4. The top right now shows the role. Try to create anything: it fails (**read-only**).
5. Account menu → **Switch back**.

Remember: a role gives **temporary** access. Same person, different hat.

## Lab 6 - Password Policy (Homework)

1. **IAM → Account settings → Password policy → Edit**.
2. Choose **Custom**: minimum length `12`, require at least one number and one non-alphanumeric character.
3. **Save changes**.

## Add These In Your Submission

- Screenshot of the three groups with their users (account ID hidden)
- Screenshots: one **allowed** and one **Access Denied**
- `notes.md`: one line per policy from Lab 4
- Optional: screenshot after **Switch role** (account ID hidden)

## If You Get Stuck

| Problem | Try this |
|---|---|
| Can't find the sign-in URL | **IAM → Dashboard** shows the account sign-in URL (or your alias URL) |
| `Cloud-Unlock-Billing` sees "access denied" on Billing | Root must turn on **IAM user and role access to Billing information** (Before You Start) |
| A test user can do everything | Check the user is only in its own group and has no other policy |
| User must change password at first sign-in | Normal if that box was ticked. Set a new strong password |
| Switch role says "invalid information" | Check the account alias and the exact role name `TrainingReadOnlyRole` |

Submit the part you completed. Add a note like:

```text
I completed the S3 and EC2 users. I got stuck on the billing user.
```

## Cleanup (end of the week)

Delete `Cloud-Unlock-S3`, `Cloud-Unlock-EC2`, `Cloud-Unlock-Billing`, `S3ReadOnlyGroup`, `EC2ReadOnlyGroup`, `BillingViewGroup` and `TrainingReadOnlyRole` when you finish the week. **Keep** `Cloud-Unlock` and `AdminGroup`.

## Official Links
| Topic | Link |
|---|---|
| Create an IAM user | https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html |
| Create IAM groups | https://docs.aws.amazon.com/IAM/latest/UserGuide/id_groups_create.html |
| Billing access for IAM users | https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/control-access-billing.html |
| Switch to a role in the console | https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-console.html |
| Password policy | https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_passwords_account-policy.html |
