# Day 1 - Account Security Lab

Goal: create a safe AWS account foundation for the next five weeks.

Exam tasks: 2.3 (root user protection, MFA), 4.2 (AWS Budgets)

## Why The Root User Is Special
The root user is the email you signed up with. It has full access to everything and cannot be limited by IAM policies.

Some tasks only the root user can do, for example:
- Change account settings: account name, root email, root password
- Close the AWS account
- Change or cancel the AWS Support plan
- Restore permissions when the only IAM admin is locked out
- Turn on IAM user access to the Billing console

Everything else should be done with an IAM user or role (Week 2).

Exam pointer: "protect the root user" = turn on MFA, do not create root access keys, do not use root for daily work, use a strong unique password.

## Practice Rule

Only the root user does this lab. Do not create any servers or storage today.

Practice in this order:

1. Install an authenticator app on your phone.
2. Turn on MFA for the root user.
3. Test MFA by signing in again.
4. Check that there are no root access keys.
5. Create a budget alert.

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

## Lab 2 - Budget Alert

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
- [ ] Budget alert created with my email
- [ ] I know which Region I work in (Mumbai `ap-south-1`)
- [ ] I know where to find Billing and Free Tier or credits

## If You Get Stuck

| Problem | Try this |
|---|---|
| "Codes not valid" | Set your phone time to automatic. Wait for a new code before typing the second one |
| Lost the phone with MFA later | Use **Troubleshoot MFA** on the sign-in page (email and phone check) |
| Budgets page shows an error | Make sure you signed in as the root user |

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
| AWS Budgets | https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-managing-costs.html |
| AWS Cost Explorer | https://docs.aws.amazon.com/cost-management/latest/userguide/ce-what-is.html |
| AWS Pricing Calculator | https://calculator.aws/ |
