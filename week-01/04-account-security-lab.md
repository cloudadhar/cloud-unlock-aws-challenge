# Day 1 - Account Security Lab

Goal: create a safe AWS account foundation for the next five weeks.

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

## If You Get Stuck
Add a screenshot of where you got stuck, write 2-3 lines, and ask in the community. Do not skip the whole week.

## Safety Note
Do not share root email, account ID, access keys, MFA QR code, OTP, payment details or detailed billing.
