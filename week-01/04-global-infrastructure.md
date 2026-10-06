# Day 2 - Global Infrastructure

## Terms
- **Region**: geographic area with multiple isolated locations (Mumbai `ap-south-1`).
- **Availability Zone (AZ)**: one or more data centres in a Region with separate power and networking.
- **Edge location**: site close to users that caches content (CloudFront).
- **Local Zone / Wavelength Zone**: compute closer to a city / inside 5G networks.

Live counts are on aws.amazon.com/about-aws/global-infrastructure. Do not memorise numbers; check the live page.

## How To Choose A Region
1. Compliance and data residency
2. Latency to users
3. Service availability
4. Cost

Exam pointer: data must stay in a country = choose a Region there. Users far away = CloudFront. High availability = multiple AZs. Region-wide disaster recovery = multiple Regions.

## Lab - Region And AZ Explorer
```bash
aws ec2 describe-regions --query "Regions[].RegionName" --output text
aws ec2 describe-regions --all-regions --query "Regions[].[RegionName,OptInStatus]" --output table
aws ec2 describe-availability-zones --region ap-south-1 --query "AvailabilityZones[].[ZoneName,ZoneId,State]" --output table
aws ec2 describe-availability-zones --region us-east-1 --query "AvailabilityZones[].ZoneName" --output text
```
Notes:
- Opt-in Regions (such as Hyderabad `ap-south-2`) must be enabled before use. Do not enable them for this lab.
- Zone names are mapped per account; zone IDs are the same for everyone.

## Deliverables
- Screenshot of the Mumbai AZ table (account ID hidden)
- Four-line Region choice for a fest-registration site for students in Pune
