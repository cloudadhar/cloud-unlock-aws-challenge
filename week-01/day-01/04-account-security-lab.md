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

## Before You Start
You need your root login, a phone with an authenticator app, and access to your email.

## Lab 1 - Secure The Root User
1. Sign in as the root user.
2. Account menu > Security credentials.
3. Multi-factor authentication > Assign MFA device. Name it `root-mfa-phone`.
4. Choose Authenticator app and scan the QR code. Do **not** screenshot the QR.
5. Enter two consecutive codes. Finish.
6. Sign out and sign in again to confirm MFA is asked.
7. Confirm there are no root access keys. Delete any you find.
8. Stop using root for daily work. We create a safer IAM user in Week 2.

Deliverables:
- Screenshot showing root MFA assigned (no QR, no codes, account ID hidden)
- Short note: why root should not be used daily

## Lab 2 - Budget Alert
1. Billing and Cost Management > Budgets > Create budget.
2. Use a template such as Zero spend or Monthly cost, or a custom cost budget. Amount: USD 5.
3. Name it `cloud-unlock-learning-budget`. Add your email for alerts.
4. Create the budget.

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
Add a screenshot of where you got stuck, write 2-3 lines, and ask in the community. Do not skip the whole week.

## Safety Note
Do not share root email, account ID, access keys, MFA QR code, OTP, payment details or detailed billing.
