# Day 1 - Account Security Lab

Goal: create a safe AWS account foundation for the next five weeks.

Exam tasks: 2.3 (root user protection, MFA, IAM users and groups), 4.2 (AWS Budgets)

In class: Labs 1 and 3 on **Day 1** (Saturday). Labs 2 and 4 at the start of **Day 2** (Sunday).

## Why The Root User Is Special
The root user is the email you signed up with. It has full access to everything and cannot be limited by IAM policies.

Some tasks only the root user can do, for example:
- Change account settings: account name, root email, root password
- Close the AWS account
- Change or cancel the AWS Support plan
- Restore permissions when the only IAM admin is locked out
- Turn on IAM user access to the Billing console

Everything else should be done with an IAM user (Lab 3 below) or an IAM role (Week 2).

Exam pointer: "protect the root user" = turn on MFA, do not create root access keys, do not use root for daily work, use a strong unique password.

## Practice Rule

Sign in as the root user for Labs 1-3. Do not create any servers or storage.

Practice in this order:

1. Install an authenticator app on your phone.
2. Turn on MFA for the root user. Test it by signing in again. (Day 1)
3. Check that there are no root access keys. (Day 1)
4. Create an IAM admin user for daily work. (Day 1)
5. Create a budget alert. (Day 2)
6. Move admin access to a group, add MFA to the IAM user, and sign in as the IAM user. (Day 2)

## Before You Start
You need:

- Your root email and password
- A phone with an authenticator app (Google Authenticator, Microsoft Authenticator or similar)
- Access to your email

## Lab 1 - Secure The Root User

Create:

- MFA device name: `root-mfa-phone`

Steps:

1. Sign in to the [AWS Console](https://console.aws.amazon.com/) as the **Root user**.
2. Click your account name at the top right. Choose **Security credentials**.
3. Find the **Multi-factor authentication (MFA)** section. Click **Assign MFA device**.
4. Device name: `root-mfa-phone`.
5. Choose **Authenticator app**. Click **Next**.
6. Click **Show QR code**. Open your authenticator app and scan it. Do **not** screenshot the QR.
7. Type the 6-digit code from the app into **MFA code 1**.
8. Wait for the code to change (about 30 seconds). Type the new code into **MFA code 2**.
9. Click **Add MFA**.

Test:

1. Click your account name → **Sign out**.
2. Sign in again as the root user.
3. AWS asks for an MFA code. Type the code from your app.

Expected result: you are signed in, and the MFA device `root-mfa-phone` is listed under **Security credentials**.

Check access keys:

1. On the same **Security credentials** page, find **Access keys**.
2. It should say there are no access keys. Do not create any.
3. If you find an old key you do not use, delete it. If you are unsure, ask in the community first.

Stop using root for daily work. We create a safer IAM user in Week 2.

Deliverables:
- Screenshot showing root MFA assigned (no QR, no codes, account ID hidden)
- Short note: why root should not be used daily

## Lab 2 - Budget Alert (Day 2, first thing in class)

Create:

- Budget name: `cloud-unlock-learning-budget`
- Amount: USD 5 (or the Zero spend template)

Steps:

1. Search `Budgets` in the Console. Open **Billing and Cost Management** → **Budgets**.
2. Click **Create budget**.
3. Choose **Use a template (simplified)**.
4. Choose **Zero spend budget**, or **Monthly cost budget** with amount `5`.
5. Budget name: `cloud-unlock-learning-budget`.
6. Email recipients: your email.
7. Click **Create budget**.

Test:

1. Go back to **Budgets**.
2. Find `cloud-unlock-learning-budget` in the list.

Expected result: the budget appears in the list with your amount.

Remember: budgets **alert** you. They do **not** stop spending. Alert emails can arrive late, so always clean up after labs.

Deliverables:
- Screenshot of the budget list
- Short note: why monitor cost from day one (budgets alert; they do not stop spending)

## Lab 3 - Create An IAM Admin User (Day 1)

Why: root is the master key. For daily work you use a separate **IAM user**, like a staff ID card instead of the owner's key.

Create:

- User name: `Cloud-Unlock` (or the name you used in class)
- Permission: `AdministratorAccess`

Steps (signed in as root):

1. Search `IAM` and open it. Left menu: **Users** → **Create user**.
2. User name: `Cloud-Unlock`.
3. Tick **Provide user access to the AWS Management Console**. If asked, choose **I want to create an IAM user**.
4. Console password: **Custom password**. Use a strong password you do not use anywhere else.
5. Click **Next**.
6. Permissions options: **Attach policies directly**. Search `AdministratorAccess` and tick it.
7. Click **Next** → **Create user**.
8. The last page shows the **Console sign-in URL**. Save it in your notes. It contains your **account ID**, so never share it or show it in a screenshot.

Expected result: `Cloud-Unlock` appears in **IAM → Users** with `AdministratorAccess`.

Deliverable: screenshot of the IAM user list (account ID hidden).

## Lab 4 - Admin Access Through A Group (Day 2)

Better approach: attach policies to **groups**, then add users to groups. 100 engineers? One group, one set of permissions. Exam pointer: "manage permissions for many users" = **IAM groups**.

Practice in this order:

1. Create group.
2. Attach policy to group.
3. Add user to group.
4. Remove the policy attached directly to the user.
5. Add MFA to the user.
6. Sign in as the user and test.

Create:

- Group: `AdminGroup`
- Policy: `AdministratorAccess`
- User: `Cloud-Unlock` (from Lab 3)
- MFA device: `iam-admin-mfa-phone`

Steps (signed in as root):

1. **IAM → User groups → Create group**. Name: `AdminGroup`.
2. Add users: tick `Cloud-Unlock`.
3. Attach permissions policies: tick `AdministratorAccess` → **Create user group**.
4. **IAM → Users → `Cloud-Unlock` → Permissions**: select `AdministratorAccess` **Attached directly** → **Remove**. The user keeps access through the group.
5. Same user → **Security credentials** → **Assign MFA device** → `iam-admin-mfa-phone` → **Authenticator app** → scan → two codes → **Add MFA**.
6. Optional, recommended: **IAM → Dashboard → AWS Account → Account alias → Create** (for example `cloudunlock-yourname`). The sign-in URL then shows the alias instead of the account ID.

Test:

- Sign out of root. Open the IAM sign-in URL and sign in as `Cloud-Unlock` with password and MFA code.
- Confirm the top right shows `Cloud-Unlock`, not root.
- Confirm **IAM → Users → `Cloud-Unlock` → Permissions** shows `AdministratorAccess` attached via `AdminGroup`.

From now on, do all practice as `Cloud-Unlock`. Root stays locked with MFA.

Add these in your submission:

- Screenshot of `AdminGroup` with `Cloud-Unlock` inside (account ID hidden).
- Short note: why permissions go on groups, not users.

## Budgets Or Cost Explorer?
| Tool | Use it to | Think of it as |
|---|---|---|
| AWS Budgets | Get an alert **before or when** spend crosses a limit | Smoke alarm |
| AWS Cost Explorer | See and analyse **past** spend and forecasts | Bank statement |
| AWS Pricing Calculator | Estimate cost **before** you build | Shopping quote |

## Account Security Checklist
Tick these in your `notes.md` (do not share any IDs):
- [ ] Root user has MFA
- [ ] No root access keys exist
- [ ] Root password is strong and stored safely (for example in a password manager)
- [ ] IAM admin user `Cloud-Unlock` created (Day 1)
- [ ] Budget alert created with my email (Day 2)
- [ ] Admin access moved to group `AdminGroup`, MFA on the IAM user, signed in as the IAM user (Day 2)
- [ ] I know which Region I work in (Mumbai `ap-south-1`)
- [ ] I know where to find Billing and Free Tier or credits

## If You Get Stuck

| Problem | Try this |
|---|---|
| "Codes not valid" | Set your phone time to automatic. Wait for a new code before typing the second one |
| Lost the phone with MFA later | Use **Troubleshoot MFA** on the sign-in page (email and phone check) |
| Budgets page shows an error | Make sure you signed in as the root user |
| IAM user cannot see Billing or Budgets | Normal by default. Do the budget as root, or (root only) Account → turn on **IAM user and role access to Billing information** |
| Forgot the IAM sign-in URL | Sign in as root → **IAM → Dashboard** shows the sign-in URL |
| Alias name already taken | Account aliases are unique worldwide. Add your name or a number |

Add a screenshot of where you got stuck, write 2-3 lines, and ask in the community. Do not skip the whole week.

```text
I turned on MFA. I got stuck creating the budget because the page showed an error.
```

## Safety Note
Do not share root email, account ID, access keys, MFA QR code, OTP, payment details or detailed billing.

## Official Links
| Topic | Link |
|---|---|
| Root user best practices | https://docs.aws.amazon.com/IAM/latest/UserGuide/root-user-best-practices.html |
| Tasks that need the root user | https://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-user.html |
| Turn on MFA for the root user | https://docs.aws.amazon.com/IAM/latest/UserGuide/enable-virt-mfa-for-root.html |
| MFA in AWS | https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa.html |
| Create an IAM user | https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html |
| Create IAM groups | https://docs.aws.amazon.com/IAM/latest/UserGuide/id_groups_create.html |
| Add or remove users in a group | https://docs.aws.amazon.com/IAM/latest/UserGuide/id_groups_manage_add-remove-users.html |
| MFA for an IAM user | https://docs.aws.amazon.com/IAM/latest/UserGuide/enable-virt-mfa-for-iam-user.html |
| Account alias | https://docs.aws.amazon.com/IAM/latest/UserGuide/console-account-alias.html |
| IAM best practices | https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html |
| AWS Budgets | https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-managing-costs.html |
| AWS Cost Explorer | https://docs.aws.amazon.com/cost-management/latest/userguide/ce-what-is.html |
| AWS Pricing Calculator | https://calculator.aws/ |
