# Cleanup checklist

- [ ] Open EC2, S3, RDS, Lambda in the Region you used and confirm nothing is left running
- [ ] Billing > Free Tier / Credits: usage looks normal
- [ ] Budget alert still active
- [ ] Closed CloudShell
Delete in reverse order of creation. Dependencies first (for example instance before security group).
