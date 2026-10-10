# Day 1 - Practical Steps (Follow Along Live)

Keep this page open during the live class. Do each step with the trainer and tick it.

Full explanations are in [03-account-setup-console-tour.md](./03-account-setup-console-tour.md) and [04-account-security-lab.md](./04-account-security-lab.md).

## Before The Practical

- [ ] AWS account created (if it is still activating, watch now and finish after class)
- [ ] Authenticator app on your phone (Google Authenticator or Microsoft Authenticator)
- [ ] Laptop browser open at https://console.aws.amazon.com/

Never show your account ID, root email, card, OTP or MFA QR code in chat or screenshots.

---

## Practical 1 - Console Tour (8:08)

Type **READY** in chat when your Console is open.

- [ ] 1. Sign in as the **Root user**.
- [ ] 2. Top right: click the **Region**. Choose **Asia Pacific (Mumbai) ap-south-1**.
- [ ] 3. Search bar: type `EC2`, open it. Click the AWS logo to go back.
- [ ] 4. Search `S3`, open it, go back.
- [ ] 5. Switch Region to **US East (N. Virginia)**. See the name change. Switch back to **Mumbai**.
- [ ] 6. Search `Billing`. Open **Billing and Cost Management**.
- [ ] 7. Left menu: open **Free Tier** or **Credits**.

You are done when: you can say which Region you are in and where your credits are.

Screenshot: `console-region.png` (Console Home with Region visible, account ID hidden).

---

## Practical 2 - Lock The Root User With MFA (8:18)

Create: MFA device `root-mfa-phone`

- [ ] 1. Top right: click your account name → **Security credentials**.
- [ ] 2. **Multi-factor authentication (MFA)** → **Assign MFA device**.
- [ ] 3. Device name: `root-mfa-phone`.
- [ ] 4. Choose **Authenticator app** → **Next**.
- [ ] 5. **Show QR code**. Scan it with your phone app. Do **not** screenshot the QR.
- [ ] 6. Type the 6-digit code into **MFA code 1**.
- [ ] 7. Wait about 30 seconds for a new code. Type it into **MFA code 2**.
- [ ] 8. Click **Add MFA**.

Test:

- [ ] 9. Account name → **Sign out**.
- [ ] 10. Sign in again as root. AWS asks for the MFA code. Type it.
- [ ] 11. **Security credentials** → **Access keys** should show none. Do not create any.

Type **BOOM** in chat when MFA works.

Screenshot: `root-mfa.png` (MFA device listed; no QR, no codes, account ID hidden).

---

## Practical 3 - Create An IAM Admin User (8:35)

Create: IAM user `Cloud-Unlock` with `AdministratorAccess`

- [ ] 1. Search `IAM`, open it. Left menu: **Users** → **Create user**.
- [ ] 2. User name: `Cloud-Unlock`.
- [ ] 3. Tick **Provide user access to the AWS Management Console**. If asked, choose **I want to create an IAM user**.
- [ ] 4. **Custom password**: strong, not used anywhere else.
- [ ] 5. **Next** → **Attach policies directly** → tick `AdministratorAccess`.
- [ ] 6. **Next** → **Create user**.
- [ ] 7. Save the **Console sign-in URL** in your notes. It contains your account ID: never share it.

Type **IAM** in chat when the user is created.

Screenshot: `iam-user.png` (IAM user list, account ID hidden).

Budget alert and the IAM group come first thing on **Day 2**.

---

## If You Get Stuck

| Problem | Try this |
|---|---|
| Account still "pending activation" | Normal, can take up to 24 hours. Watch now, finish later. |
| MFA says "codes not valid" | Set your phone time to automatic. Use two **different** codes. |
| "User name already exists" | Pick another name, for example `Cloud-Unlock-2`. |
| Wrong Region on screen | Top right → choose Mumbai again. |

Type **STUCK** in chat with one line about the problem. The trainer helps after the class.

---

## After Class

- [ ] 3 screenshots saved: `console-region.png`, `root-mfa.png`, `iam-user.png`
- [ ] Career notes in `notes.md` ([02-well-architected-and-careers.md](./02-well-architected-and-careers.md))
- [ ] Connected with 3 classmates on LinkedIn
- [ ] LinkedIn post with `#CloudUnlock` ([10-linkedin-post.md](../10-linkedin-post.md))

<div align="center">

[Day 1 guide](./README.md) | [Day 2 steps](../day-02/practical-steps.md)

</div>
