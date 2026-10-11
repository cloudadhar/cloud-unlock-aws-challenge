# Day 2 - Practical Steps (Follow Along Live)

Keep this page open during the live class. Do each step with the trainer and tick it.

Full explanations are in [04-account-security-lab.md](../day-01/04-account-security-lab.md), [05-iam-basics.md](./05-iam-basics.md) and [06-iam-hands-on-lab.md](./06-iam-hands-on-lab.md).

## Before The Practical

- [ ] Root MFA and IAM user `Cloud-Unlock` from Day 1 are done
- [ ] Signed in **as root** at https://console.aws.amazon.com/ (for Practicals A and B only), Region = **Mumbai**
- [ ] A private or incognito window ready (to test the learner users)

Never show your account ID, access keys, OTP or MFA QR code.

---

## Practical A - Budget Alert (7:05)

Create: budget `cloud-unlock-learning-budget` (as root)

- [ ] 1. Search `Budgets`. Open **Billing and Cost Management** → **Budgets**.
- [ ] 2. **Create budget** → **Use a template (simplified)**.
- [ ] 3. **Zero spend budget**, or **Monthly cost budget** with amount `5` USD.
- [ ] 4. Budget name: `cloud-unlock-learning-budget`.
- [ ] 5. Email recipients: your email.
- [ ] 6. **Create budget**. Check it is in the Budgets list.

Type **BUDGET** in chat. Remember: a budget **alerts**, it does **not** stop spending.

Screenshot: `budget-alert.png`.

---

## Practical B - AdminGroup, MFA And Sign In As Cloud-Unlock (7:15)

Create: group `AdminGroup`, MFA device `iam-admin-mfa-phone` (as root)

- [ ] 1. **IAM → User groups → Create group** → `AdminGroup`.
- [ ] 2. Add users: tick `Cloud-Unlock`.
- [ ] 3. Attach `AdministratorAccess` → **Create user group**.
- [ ] 4. **IAM → Users → `Cloud-Unlock` → Permissions**: select `AdministratorAccess` **Attached directly** → **Remove**.
- [ ] 5. Same user → **Security credentials** → **Assign MFA device** → `iam-admin-mfa-phone` → **Authenticator app** → scan → two codes → **Add MFA**.
- [ ] 6. **IAM → Dashboard → Account alias → Create** (for example `cloudunlock-yourname`). The sign-in URL now hides your account ID.
- [ ] 7. **Sign out of root.** Open the alias sign-in URL. Sign in as `Cloud-Unlock` with password + MFA code.
- [ ] 8. Check: top right shows `Cloud-Unlock`, not root.

Type **ADMIN** in chat. From now on, **everything is done as `Cloud-Unlock`**.

Screenshot: `iam-group.png`.

---

## Practical 1 - Read User And Write User (7:45)

Create (as `Cloud-Unlock`):

| Group | Policy | User |
|---|---|---|
| `S3ReadOnlyGroup` | `AmazonS3ReadOnlyAccess` | `Cloud-Unlock-RUser` |
| `S3FullAccessGroup` | `AmazonS3FullAccess` | `Cloud-Unlock-WUser` |

- [ ] 1. **IAM → User groups → Create group** → `S3ReadOnlyGroup` → attach `AmazonS3ReadOnlyAccess` → **Create user group**.
- [ ] 2. **IAM → Users → Create user** → `Cloud-Unlock-RUser` → console access → **Custom password** → **Next**.
- [ ] 3. **Add user to group** → `S3ReadOnlyGroup` → **Next** → **Create user**.
- [ ] 4. Repeat for `S3FullAccessGroup` / `AmazonS3FullAccess` / `Cloud-Unlock-WUser`.

---

## Practical 2 - Test Allowed vs Denied (8:00)

- [ ] 1. Incognito window → alias sign-in URL → sign in as `Cloud-Unlock-RUser`.
- [ ] 2. Open **S3**: the list opens (**allowed**).
- [ ] 3. **Create bucket** → try to create → **Access Denied**.
- [ ] 4. Sign out. Sign in as `Cloud-Unlock-WUser` → **Create bucket** `cloud-unlock-<yourname>-wuser-test` → it **works** (allowed).
- [ ] 5. Delete that bucket now (select → **Delete** → type the name).

Type **DENIED** in chat when you see the error.

Screenshots: `iam-allowed.png`, `iam-denied.png`.

---

## Practical 3 - AWS CLI In CloudShell (8:10)

No access keys needed: CloudShell uses the user you are signed in with (`Cloud-Unlock`). On your own laptop, `aws configure` asks for an access key; never share it or put it on GitHub.

- [ ] 1. Region **Mumbai** → click the **CloudShell** icon `>_` next to the search bar. Wait for it to load.
- [ ] 2. Who am I? (the account ID is hidden with `sed`)

```bash
aws --version
aws sts get-caller-identity --query Arn --output text | sed -E 's/[0-9]{12}/XXXXXXXXXXXX/'
```

Expected: `arn:aws:iam::XXXXXXXXXXXX:user/Cloud-Unlock`

- [ ] 3. See today's IAM work:

```bash
aws iam list-users --query "Users[].UserName" --output table
aws iam list-groups --query "Groups[].GroupName" --output table
aws iam list-attached-group-policies --group-name AdminGroup --output table
aws iam list-attached-user-policies --user-name Cloud-Unlock
```

Expected: the last command shows an **empty** list. `Cloud-Unlock` gets admin access from `AdminGroup`.

- [ ] 4. Regions and AZs (Day 1 revision):

```bash
aws ec2 describe-availability-zones --region ap-south-1 --query "AvailabilityZones[].[ZoneName,ZoneId]" --output table
```

- [ ] 5. S3 from the CLI (replace `<yourname>`; bucket names are unique worldwide):

```bash
aws s3 mb s3://cloud-unlock-<yourname>-cli-demo --region ap-south-1
echo "Hello from Cloud Unlock" > hello.txt
aws s3 cp hello.txt s3://cloud-unlock-<yourname>-cli-demo/
aws s3 ls s3://cloud-unlock-<yourname>-cli-demo/
```

- [ ] 6. Open **S3** in the Console: the same bucket and file are there.
- [ ] 7. Clean up now:

```bash
aws s3 rb s3://cloud-unlock-<yourname>-cli-demo --force
```

Type **CLI** in chat when your bucket is created and deleted.

Screenshot: `cli-output.png` (masked ARN and IAM lists).

---

## Practical 4 - Custom Policy And Switch Role (8:30, quick)

Back in the normal window as `Cloud-Unlock`:

- [ ] 1. **IAM → Policies → Create policy → JSON** → paste:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    { "Effect": "Allow", "Action": ["ec2:Describe*"], "Resource": "*" }
  ]
}
```

- [ ] 2. **Next** → name `CustomEC2DescribeOnly` → **Create policy**.
- [ ] 3. **IAM → Roles → Create role** → **AWS account** → **This account** → **Next**.
- [ ] 4. Tick `ReadOnlyAccess` → **Next** → name `TrainingReadOnlyRole` → **Create role**.
- [ ] 5. Top right account menu → **Switch role** → account: your alias → role: `TrainingReadOnlyRole` → **Switch role**.
- [ ] 6. Try to create anything: denied (read-only).
- [ ] 7. Account menu → **Switch back**.

Type **ROLE** in chat when you switched.

---

## Homework - Password Policy

- [ ] **IAM → Account settings → Password policy → Edit** → **Custom** → minimum length `12`, require a number and a symbol → **Save changes**.

---

## If You Get Stuck

| Problem | Try this |
|---|---|
| Budgets page shows an error | Create the budget as root. |
| Alias name already taken | Add your name or a number. |
| Switch role says "invalid information" | Check the alias and the exact role name `TrainingReadOnlyRole`. |
| `Cloud-Unlock-RUser` can do everything | Make sure it is only in `S3ReadOnlyGroup`. |
| MFA "codes not valid" | Set phone time to automatic; two **different** codes. |
| CloudShell keeps loading | Wait 1-2 minutes, refresh, Region = Mumbai. |
| `BucketAlreadyExists` | Bucket names are unique worldwide: add a number. |

Type **STUCK** in chat with one line about the problem.

---

## After Class

- [ ] Screenshots: `budget-alert.png`, `iam-group.png`, `iam-allowed.png`, `iam-denied.png`, `cli-output.png`
- [ ] Password policy set (homework above)
- [ ] `custom-ec2-describe-only.json` saved in `code-or-policies/`
- [ ] Week 1 submission PR ([09-submission-format.md](../09-submission-format.md))
- [ ] LinkedIn post with `#CloudUnlock`
- [ ] End of week: delete `Cloud-Unlock-RUser`, `Cloud-Unlock-WUser`, the two S3 groups, `CustomEC2DescribeOnly`, `TrainingReadOnlyRole`, any `cli-demo` bucket. Keep `Cloud-Unlock` and `AdminGroup`.

<div align="center">

[Day 2 guide](./README.md) | [Day 1 steps](../day-01/practical-steps.md)

</div>
