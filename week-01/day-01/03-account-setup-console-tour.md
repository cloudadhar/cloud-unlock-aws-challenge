# Day 1 - Account Setup and Console Tour

Exam tasks: 3.1 (ways to access AWS), 4.3 (AWS Support plans)

## Practice Rule

Use your **own** AWS account. Never share your email, password, OTP, card or account ID.

Practice in this order:

1. Create your AWS account (before the live class).
2. Sign in as the root user.
3. Tour the Console.
4. Take one safe screenshot.

## Lab 1 - Create Your AWS Account
Please do this **before the Day 1 live class**. Verification and activation can take time. Skip if you already have an account.

1. Open [aws.amazon.com](https://aws.amazon.com/) and choose **Create an AWS Account**.
2. Enter your personal email and an account name, for example `cloudadhar-learning`.
3. Open your email, copy the verification code and paste it.
4. Create a strong, unique root password. Save it in a password manager.
5. Choose the **Free plan** for learning. It gives credits for a limited time. Check the Billing page for current terms.
6. Choose **Personal**. Enter your contact details. Accept the agreement.
7. Add a payment method. AWS uses it to verify identity. Never share these details.
8. Verify your phone by SMS or voice call.
9. Choose the **Basic support** plan. It is free.
10. Wait for activation. It takes minutes, sometimes up to 24 hours.
11. Go to the [AWS Console](https://console.aws.amazon.com/). Choose **Root user** and sign in.

Expected result: you see **Console Home**.

Screens and plan names can change. Follow the on-screen text.

## Lab 2 - Console Tour

Test:

1. Look at the top right. Find the **Region** name.
2. Click it and choose **Asia Pacific (Mumbai) ap-south-1**.
3. Click the search bar at the top. Type `EC2` and open it. Click the AWS logo to go back.
4. Search `S3` and open it. Go back.
5. Switch the Region to **US East (N. Virginia) us-east-1**. Notice the Region name change. Switch back to **Mumbai**.
6. Search `Billing` and open **Billing and Cost Management**.
7. Find **Free Tier** or **Credits** in the left menu. Look at what is used and what is left.
8. Click **Services** (or the grid icon). Find one service in each group: Compute, Storage, Database, Networking, Security.

Expected result: you can say which Region you are in and where to find your credits.

Add to your `notes.md`:

```text
My Region:
One service each - Compute: / Storage: / Database: / Networking: / Security:
What surprised me in the Console:
```

## Deliverables
- Screenshot of Console Home with the Region visible (account ID hidden)
- One sentence: what surprised you in the Console?

## If You Get Stuck

| Problem | Try this |
|---|---|
| No OTP or SMS | Wait 2 minutes, retry, or choose voice call |
| Card verification fails | Try another card or bank. Never post card details in chat |
| Account "pending activation" | Normal. Wait up to 24 hours, then sign in again |
| Console in another language | Gear icon (Settings) → Language |

Submit what you completed with a note:

```text
My account is still pending activation. I watched the Console tour and will finish tomorrow.
```

Next: secure your account right away in [04-account-security-lab.md](./04-account-security-lab.md).

## Official Links
| Topic | Link |
|---|---|
| Create and activate an AWS account | https://repost.aws/knowledge-center/create-and-activate-aws-account |
| Getting started with your AWS account | https://docs.aws.amazon.com/accounts/latest/reference/getting-started.html |
| AWS Free Tier | https://aws.amazon.com/free/ |
| AWS Free Tier plans and credits | https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/free-tier-plans.html |
| AWS Management Console guide | https://docs.aws.amazon.com/awsconsolehelpdocs/latest/gsg/what-is.html |
| AWS Support plans | https://aws.amazon.com/premiumsupport/plans/ |
