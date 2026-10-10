# Day 2 - Practical Steps (Follow Along Live)

Keep this page open during the live class. Do each step with the trainer and tick it.

Full explanations are in [05-global-infrastructure.md](./05-global-infrastructure.md) and [06-shared-responsibility.md](./06-shared-responsibility.md).

## Before The Practical

- [ ] Root MFA and `cloud-unlock-learning-budget` from Day 1 are done
- [ ] Signed in at https://console.aws.amazon.com/ with Region = **Mumbai**

Never run or post `aws sts get-caller-identity`; it shows your account ID. Do not enable any new Region.

---

## Practical 1 - CloudShell Region And AZ Explorer (7:40)

- [ ] 1. Click the **CloudShell** icon `>_` next to the search bar (or search `CloudShell`). Wait for it to load.
- [ ] 2. Check the CLI:

```bash
aws --version
aws configure list
```

Expected: a version like `aws-cli/2.x.x`. No access keys were typed.

- [ ] 3. List Regions:

```bash
aws ec2 describe-regions --query "Regions[].RegionName" --output text
```

Expected: you can find `ap-south-1`. Type **MUMBAI** in chat.

- [ ] 4. See opt-in Regions:

```bash
aws ec2 describe-regions --all-regions --query "Regions[].[RegionName,OptInStatus]" --output table
```

Expected: some show `not-opted-in`, for example `ap-south-2`. Do **not** enable them.

- [ ] 5. List Mumbai Availability Zones:

```bash
aws ec2 describe-availability-zones --region ap-south-1 --query "AvailabilityZones[].[ZoneName,ZoneId,State]" --output table
```

Expected: several AZs, each `available`. Take your screenshot here.

- [ ] 6. Compare with N. Virginia:

```bash
aws ec2 describe-availability-zones --region us-east-1 --query "AvailabilityZones[].ZoneName" --output text
```

- [ ] 7. Close CloudShell.

Screenshot: `region-az-output.png` (Region list and Mumbai AZ table, account ID hidden).

---

## Practical 2 - AWS Health Dashboard (8:05)

- [ ] 1. Search `Health`. Open **AWS Health Dashboard**.
- [ ] 2. **Service health** → filter **Asia Pacific (Mumbai)**.
- [ ] 3. **Your account health** → check open issues and scheduled changes.
- [ ] 4. Write one line in `notes.md`: what did it show for Mumbai?

Then write your Region choice for a shopping app like Flipkart or Myntra (customer data must stay in India):

```text
Compliance:
Latency:
Service availability:
Cost:
My Region choice:
```

---

## Practical 3 - AWS Artifact (8:35)

- [ ] 1. Search `Artifact`. Open **AWS Artifact**.
- [ ] 2. Left menu: **Reports**.
- [ ] 3. Search `ISO`, then `SOC`.
- [ ] 4. Click one report. Read its title and description.
- [ ] 5. Do **not** download or accept anything.
- [ ] 6. Write one line in `notes.md`: the report name and who might ask for it (a college, a bank client, an auditor).

---

## If You Get Stuck

| Problem | Try this |
|---|---|
| CloudShell keeps loading | Wait 1-2 minutes, refresh. Check the Region is Mumbai. |
| `aws configure list` shows no keys | That is normal in CloudShell. |
| Your `ap-south-1a` differs from a friend's | Compare the **ZoneId** column instead. |
| `UnauthorizedOperation` error | Sign in as root for this lab, or follow the trainer's screen. |
| Artifact asks you to accept terms | Do not accept. Reading the list is enough. |

Type **STUCK** in chat with one line about the problem.

---

## After Class

- [ ] Screenshot `region-az-output.png` saved
- [ ] Health Dashboard line, Region choice, card sort answers and Artifact report in `notes.md`
- [ ] Week 1 submission PR started ([09-submission-format.md](../09-submission-format.md))
- [ ] LinkedIn post with `#CloudUnlock`

<div align="center">

[Day 2 guide](./README.md) | [Day 1 steps](../day-01/practical-steps.md)

</div>
