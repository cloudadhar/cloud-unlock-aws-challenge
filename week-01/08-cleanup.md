# Week 1 Cleanup

Cleanup protects you from surprise bills.

## Resources This Week
Week 1 creates no billable resources. Nothing to delete except anything you launched by mistake.

## Delete At The End Of The Week
- IAM users `Cloud-Unlock-RUser`, `Cloud-Unlock-WUser`
- Groups `S3ReadOnlyGroup`, `S3FullAccessGroup`
- Policy `CustomEC2DescribeOnly`
- Role `TrainingReadOnlyRole`

## Keep These Enabled
- Root MFA
- Budget alert (`cloud-unlock-learning-budget`)
- IAM user `Cloud-Unlock` with MFA, in group `AdminGroup` (you use it every week)

## Final Check
- [ ] No access keys shared publicly
- [ ] `Cloud-Unlock` has no access keys (console login only this week)
- [ ] No policy attached directly to `Cloud-Unlock`; access comes from `AdminGroup`
- [ ] No secrets committed to GitHub
- [ ] Screenshots hide account ID, email and QR codes
- [ ] EC2, S3, RDS dashboards in Mumbai show nothing unexpected

If unsure whether something is safe to delete, ask before deleting it.
