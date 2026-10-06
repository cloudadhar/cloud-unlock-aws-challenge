# Day 1 - Account Setup, Console Tour and CloudShell

## Lab 1 - Create Your AWS Account
Skip if you already have an account.
1. Open aws.amazon.com and choose Create an AWS Account.
2. Enter your personal email and an account name (for example `cloudadhar-learning`). Verify the email code.
3. Create a strong, unique root password.
4. Choose the Free plan for learning (credits; check Billing for current terms).
5. Choose Personal, enter contact details, accept the agreement.
6. Add a payment method. AWS uses it to verify identity. Never share the details.
7. Verify your phone by SMS or voice.
8. Choose the Basic support plan.
9. Wait for activation (minutes, sometimes up to 24 hours). Sign in as Root user.
Screens and plan names can change; follow the on-screen text.

## Lab 2 - Console Tour
1. Note the Region at the top right.
2. Search `EC2`, open it, go back. Search `S3`.
3. Switch Region: Mumbai `ap-south-1` -> N. Virginia `us-east-1` -> Mumbai.
4. Open Billing and Cost Management and find Free Tier or Credits.
5. Name one service each in Compute, Storage, Database, Networking, Security.

## Lab 3 - CloudShell
Open CloudShell (terminal icon) in Mumbai and run:

```bash
aws --version
aws configure list
aws ec2 describe-regions --query "Regions[].RegionName" --output table
aws ec2 describe-availability-zones --query "AvailabilityZones[].ZoneName" --output text
```

Do not post `aws sts get-caller-identity` output; it shows your account ID.

## Deliverables
- Screenshot of Console Home with the Region visible (account ID hidden)
- Screenshot of the Region list output
- One sentence: what surprised you in the Console?
