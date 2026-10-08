# Day 2 - Shared Responsibility Model

Exam tasks: 2.1 (shared responsibility), 2.2 (compliance and governance)

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

## Controls: Inherited, Shared, Customer
| Type | Meaning | Examples |
|---|---|---|
| Inherited | AWS does it fully; you inherit it | Physical and environmental security of data centres |
| Shared | Both do their part, each in its own layer | **Patch management** (AWS patches infrastructure, you patch your guest OS and apps), **configuration management**, **awareness and training** |
| Customer-specific | Only you | Your data, who has access, which Region stores it |

Exam pointer: the more managed the service (EC2 -> RDS -> Lambda), the less you manage.

## Compliance: Where To Find The Proof
- **AWS Artifact**: free, self-service portal for AWS compliance reports (such as ISO and SOC) and agreements.
- **AWS Compliance Programs** (aws.amazon.com/compliance): which standards AWS meets by industry and country.
- AWS being compliant does **not** make your app compliant. You still configure your part.

## Lab - Find A Compliance Report In AWS Artifact
1. Search `Artifact` in the Console and open AWS Artifact.
2. Open **Reports** and search for `ISO` or `SOC`.
3. Read the title and description of one report. You do not need to download or accept anything.

Deliverable: one line naming a report you found and who might ask for it (for example, a college or bank client).

## Activity - Card Sort
Write A (AWS) or C (Customer) for each. Try first, then open the answers below.

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

<details>
<summary><b>Show answers</b></summary>

| # | Answer | Why |
|:-:|:-:|---|
| 1 | A | Physical hardware |
| 2 | C | Access to your data |
| 3 | A | Physical security |
| 4 | C | Guest OS on EC2 is yours |
| 5 | A | RDS is managed; AWS patches the engine |
| 6 | C | You choose to encrypt your data |
| 7 | A | Global network |
| 8 | C | Your IAM users and passwords |
| 9 | C | Your firewall rules |
| 10 | A | Lambda is serverless; AWS manages the runtime |
| 11 | C | You choose the Region |
| 12 | A | Virtualisation layer |

</details>

Deliverable: your 12 answers in `notes.md`, with one line on any you got wrong and why.
