# Day 2 - Shared Responsibility Model

> AWS secures the cloud. You secure what you build in the cloud.

| | AWS | You |
|---|---|---|
| Headline | Security **of** the cloud | Security **in** the cloud |
| Examples | Data centres, hardware, hypervisor, global network | Data, IAM, firewall rules, EC2 guest OS patching |

## Responsibility Shifts By Service

| Service | AWS handles | You handle |
|---|---|---|
| EC2 | Hardware, virtualisation | Guest OS, patches, apps, security groups, data |
| RDS | Hardware, OS, database patching | Data, access, network access, settings |
| Lambda | Servers, OS, runtime | Code, permissions, data |
| S3 | Hardware, service durability | Bucket permissions, encryption choice, content |

## Activity - Card Sort
Write A (AWS) or C (Customer) for each. Answers are in the quiz prep file after you try.

1. Replacing a failed disk in a data centre
2. Deciding who can read your S3 bucket
3. Physical security of the building
4. Patching the OS on your EC2 instance
5. Patching the database engine on RDS
6. Encrypting your customer data
7. Keeping the global network cables running
8. Rotating your IAM user passwords
9. Configuring your security group rules
10. Keeping the Lambda runtime up to date
11. Deciding which Region stores your data
12. Hypervisor security

Deliverable: your 12 answers in `notes.md`.
