# Day 2 - Practical Steps (Follow Along Live)

Keep this page open during the live class. Do each step with the trainer and tick it.

Full explanations are in [04-account-security-lab.md](../day-01/04-account-security-lab.md), [05-iam-basics.md](./05-iam-basics.md) and [06-iam-hands-on-lab.md](./06-iam-hands-on-lab.md).

## Before The Practical

- [ ] Root MFA and IAM user `Cloud-Unlock` from Day 1 are done
- [ ] Signed in **as root** at https://console.aws.amazon.com/ (for Practicals A and B only), Region = **Mumbai**
- [ ] A private or incognito window ready (to test the learner users)

Never show your account ID, access keys, OTP or MFA QR code.

---

## Practical A - Budget Alert + Billing Access (7:08)

Create: budget `cloud-unlock-learning-budget`, and turn on IAM access to billing (as root)

- [ ] 1. Search `Budgets`. Open **Billing and Cost Management** → **Budgets**.
- [ ] 2. **Create budget** → **Use a template (simplified)**.
- [ ] 3. **Zero spend budget**, or **Monthly cost budget** with amount `5` USD.
- [ ] 4. Budget name: `cloud-unlock-learning-budget`.
- [ ] 5. Email recipients: your email.
- [ ] 6. **Create budget**. Check it is in the Budgets list.
- [ ] 7. Account name (top right) → **Account** → **IAM user and role access to Billing information** → **Edit** → tick **Activate IAM Access** → **Update**. (Needed for the billing user later.)

Type **BUDGET** in chat. Remember: a budget **alerts**, it does **not** stop spending.

Screenshot: `budget-alert.png`.

---

## Practical B - AdminGroup, MFA And Sign In As Cloud-Unlock (7:20)

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

## Practical 1 - S3 Read-Only User (7:55, everyone)

Create (as `Cloud-Unlock`): group `S3ReadOnlyGroup` + policy `AmazonS3ReadOnlyAccess` + user `Cloud-Unlock-S3`

- [ ] 1. **IAM → User groups → Create group** → `S3ReadOnlyGroup` → attach `AmazonS3ReadOnlyAccess` → **Create user group**.
- [ ] 2. **IAM → Users → Create user** → `Cloud-Unlock-S3` → console access → **Custom password** → **Next**.
- [ ] 3. **Add user to group** → `S3ReadOnlyGroup` → **Next** → **Create user**.
- [ ] 4. Incognito window → alias sign-in URL → sign in as `Cloud-Unlock-S3`.
- [ ] 5. Open **S3**: the list opens (**allowed**).
- [ ] 6. **Create bucket** → try → **Access Denied**.

Type **DENIED** in chat when you see the error.

Screenshots: `iam-allowed.png`, `iam-denied.png`.

---

## Practical 2 - EC2 Read-Only User (8:10)

Create: group `EC2ReadOnlyGroup` + policy `AmazonEC2ReadOnlyAccess` + user `Cloud-Unlock-EC2`

- [ ] 1. Same steps as Practical 1, with the EC2 names above.
- [ ] 2. Sign in as `Cloud-Unlock-EC2` → **EC2** dashboard opens (**allowed**).
- [ ] 3. **Launch instance** → keep defaults → launch → fails (**denied**). Nothing is created.

If you are behind, watch the trainer and do this at home.

---

## Practical 3 - Billing Read-Only User (8:20)

Create: group `BillingViewGroup` + policy `AWSBillingReadOnlyAccess` + user `Cloud-Unlock-Billing`

- [ ] 1. Same steps as Practical 1, with the billing names above.
- [ ] 2. Sign in as `Cloud-Unlock-Billing` → **Billing and Cost Management** opens (**allowed**).
- [ ] 3. Open **S3** or **EC2** → not authorized (**denied**).

If Billing says access denied, step 7 of Practical A (root) was not done.

---

## Trainer Demo - Switch Role (8:30, watch)

The trainer switches into a read-only role `TrainingReadOnlyRole`. Same person, different hat. Try it at home: Lab 5 in [06-iam-hands-on-lab.md](./06-iam-hands-on-lab.md).

---

## Homework

- [ ] Lab 4: open the three policies' **JSON** tabs and write one line each in `notes.md`.
- [ ] Lab 6: password policy (**IAM → Account settings → Password policy → Edit** → length 12, number, symbol).
- [ ] Optional: Lab 5, switch role.

---

## If You Get Stuck

| Problem | Try this |
|---|---|
| Budgets page shows an error | Create the budget as root. |
| Alias name already taken | Add your name or a number. |
| A test user can do everything | It must be only in its own group. |
| Billing user sees access denied on Billing | Root must activate IAM access to Billing (Practical A step 7). |
| MFA "codes not valid" | Set phone time to automatic; two **different** codes. |

Type **STUCK** in chat with one line about the problem.

---

## After Class

- [ ] Screenshots: `budget-alert.png`, `iam-group.png`, `iam-allowed.png`, `iam-denied.png`
- [ ] Week 1 submission PR ([09-submission-format.md](../09-submission-format.md))
- [ ] LinkedIn post with `#CloudUnlock`
- [ ] End of week: delete `Cloud-Unlock-S3`, `Cloud-Unlock-EC2`, `Cloud-Unlock-Billing`, their three groups and `TrainingReadOnlyRole`. Keep `Cloud-Unlock` and `AdminGroup`.

<div align="center">

[Day 2 guide](./README.md) | [Day 1 steps](../day-01/practical-steps.md)

</div>
