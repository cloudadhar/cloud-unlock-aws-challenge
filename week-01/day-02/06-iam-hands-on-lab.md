# Day 2 - IAM Hands-On Lab

Today, practise least privilege using IAM users, groups, policies and a role, then use the AWS CLI in CloudShell.

Exam tasks: 2.3 (AWS access management), 3.1 (ways to access AWS: Console, CLI, SDK, IaC)

## Practice Rule

Create only read-only access in this lab. Do not give full access unless asked. Do Labs 2 and 4 of [04-account-security-lab.md](../day-01/04-account-security-lab.md) first (budget and `AdminGroup`), then work as `Cloud-Unlock`.

Practice in this order:

1. Create group.
2. Attach read-only policy to group.
3. Create user.
4. Add user to group.
5. Test allowed access.
6. Test denied access.

## Lab 1 - S3 Read-Only Access

Create:

- Group: `S3ReadOnlyGroup`
- Policy: `AmazonS3ReadOnlyAccess`
- User: `Cloud-Unlock-RUser`

Steps (as `Cloud-Unlock`):

1. **IAM → User groups → Create group** → `S3ReadOnlyGroup` → attach `AmazonS3ReadOnlyAccess` → **Create user group**.
2. **IAM → Users → Create user** → `Cloud-Unlock-RUser` → tick **Provide user access to the AWS Management Console** → **Custom password** → **Next**.
3. Permissions options: **Add user to group** → tick `S3ReadOnlyGroup` → **Next** → **Create user**.

Test:

- Open a private or incognito window. Sign in with your alias sign-in URL as `Cloud-Unlock-RUser`.
- Open **S3**. The bucket list opens (**allowed**).
- Click **Create bucket** and try to create one. It fails (**denied**).
- Capture the `Access Denied` message.

## Lab 2 - S3 Write Access

Create:

- Group: `S3FullAccessGroup`
- Policy: `AmazonS3FullAccess`
- User: `Cloud-Unlock-WUser`

Test:

- Sign in as `Cloud-Unlock-WUser`.
- **Create bucket** `cloud-unlock-<yourname>-wuser-test` (Region Mumbai, defaults). It **works** (**allowed**).
- Same action, two users: `Cloud-Unlock-RUser` is denied, `Cloud-Unlock-WUser` is allowed. Policies decide.
- Delete the bucket right away: select it → **Delete** → type the name → **Delete bucket**.

## Lab 3 - Read A Policy (JSON)

1. **IAM → Policies** → search `AmazonS3ReadOnlyAccess` → open it → **JSON** tab.
2. Find `Effect`, `Action` and `Resource`.
3. Write one line in `notes.md`: what does this policy allow?

## Lab 4 - Custom Policy And A Role (Switch Role)

Create a customer managed policy:

```text
CustomEC2DescribeOnly
```

1. **IAM → Policies → Create policy → JSON** → paste:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    { "Effect": "Allow", "Action": ["ec2:Describe*"], "Resource": "*" }
  ]
}
```

2. **Next** → name `CustomEC2DescribeOnly` → **Create policy**.

Create a role:

- Role: `TrainingReadOnlyRole`
- Trusted entity: **AWS account** → **This account**
- Policy: `ReadOnlyAccess`

3. **IAM → Roles → Create role** → **AWS account** → **This account** → **Next** → tick `ReadOnlyAccess` → **Next** → name `TrainingReadOnlyRole` → **Create role**.

Test (as `Cloud-Unlock`):

- Top right account menu → **Switch role**.
- Account: your account alias. Role: `TrainingReadOnlyRole`. → **Switch role**.
- The top right now shows the role. Try to create anything: it fails (**read-only**).
- Account menu → **Switch back**.

Remember: a role gives **temporary** access. Same person, different hat.

## Lab 5 - Password Policy

1. **IAM → Account settings → Password policy → Edit**.
2. Choose **Custom**: minimum length `12`, require at least one number and one non-alphanumeric character.
3. **Save changes**.

## Lab 6 - AWS CLI In CloudShell

The CLI is one of the **four ways to access AWS**: Console (click), CLI (type), SDK (code), Infrastructure as Code (template). All of them call the same AWS APIs.

On your own laptop, `aws configure` asks for an **Access key ID**, **Secret access key**, **Region** and **output format**. Access keys are for the CLI and code only: never share them, never put them on GitHub, never create them for root. Today we use **CloudShell**, which needs no keys.

Run in CloudShell (Region Mumbai), signed in as `Cloud-Unlock`:

```bash
aws sts get-caller-identity --query Arn --output text | sed -E 's/[0-9]{12}/XXXXXXXXXXXX/'
aws iam list-users --query "Users[].UserName" --output table
aws iam list-attached-user-policies --user-name Cloud-Unlock
aws s3 mb s3://cloud-unlock-<yourname>-cli-demo --region ap-south-1
echo "Hello from Cloud Unlock" > hello.txt
aws s3 cp hello.txt s3://cloud-unlock-<yourname>-cli-demo/
aws s3 ls s3://cloud-unlock-<yourname>-cli-demo/
aws s3 rb s3://cloud-unlock-<yourname>-cli-demo --force
```

Expected:

- The masked ARN ends with `user/Cloud-Unlock`. Never share the unmasked output; it shows your account ID.
- `list-attached-user-policies` is empty, because access comes from `AdminGroup`.
- The bucket is created, the file is listed, then the bucket is removed.

## Add These In Your Submission

- Screenshot of `S3ReadOnlyGroup` with `Cloud-Unlock-RUser` (account ID hidden)
- Screenshot of one **allowed** and one **Access Denied**
- `code-or-policies/custom-ec2-describe-only.json` with your policy
- Screenshot of the role after **Switch role** (account ID hidden)
- Screenshot of your CLI output (masked ARN and IAM lists)

## If You Get Stuck

| Problem | Try this |
|---|---|
| Can't find the sign-in URL for `Cloud-Unlock-RUser` | **IAM → Dashboard** shows the account sign-in URL (or your alias URL) |
| Switch role says "invalid information" | Check the account alias and the exact role name `TrainingReadOnlyRole` |
| `Cloud-Unlock-RUser` must change password at first sign-in | Normal if that box was ticked. Set a new strong password |
| You can still do everything as `Cloud-Unlock-RUser` | Check the user is only in `S3ReadOnlyGroup` and has no other policy |

Submit the part you completed. Add a note like:

```text
I completed S3 read-only access. I got stuck while testing switch role.
```

## Cleanup (end of the week)

Delete `Cloud-Unlock-RUser`, `Cloud-Unlock-WUser`, `S3ReadOnlyGroup`, `S3FullAccessGroup`, `CustomEC2DescribeOnly`, `TrainingReadOnlyRole` and any `cli-demo` bucket when you finish the week. **Keep** `Cloud-Unlock` and `AdminGroup`.

## Official Links
| Topic | Link |
|---|---|
| Create an IAM user | https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html |
| Create IAM groups | https://docs.aws.amazon.com/IAM/latest/UserGuide/id_groups_create.html |
| Create a policy (JSON) | https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create-console.html |
| Switch to a role in the console | https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-console.html |
| Password policy | https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_passwords_account-policy.html |
| AWS CloudShell | https://docs.aws.amazon.com/cloudshell/latest/userguide/welcome.html |
| AWS CLI user guide | https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html |
