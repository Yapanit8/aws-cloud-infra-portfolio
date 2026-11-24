# AWS Cloud Infrastructure Portfolio

Hands-on AWS projects I'm building to learn cloud infrastructure, one project at a time, with documentation of what worked, what didn't, and what I'd do differently.

## About

I'm Karl, an AWS re/Start graduate (Batch 30) and full-stack web developer moving into cloud engineering. I'm working toward a Cloud Engineer role and preparing for the AWS Certified Cloud Practitioner exam on December 11, 2026.

This repo is where I build, break, fix, and document AWS projects that go from beginner to intermediate. Each project builds on the one before it.

## Projects

| # | Project | Key AWS Services | Status | Docs |
|---|---|---|---|---|
| 01 | Secure Account Baseline | IAM, MFA, CloudTrail, AWS Budgets | Planned | - |
| 02 | Static Website Hosting | S3, CloudFront | Planned | - |
| 03 | VPC Networking Fundamentals | VPC, Subnets, Route Tables, Security Groups, NACLs | Planned | - |
| 04 | Infrastructure as Code | CloudFormation | Planned | - |
| 05 | Highly Available Web App | EC2, Application Load Balancer, Auto Scaling, Multi-AZ | Planned | - |
| 06 | Serverless API | Lambda, API Gateway, DynamoDB | Planned | - |
| 07 | Monitoring and Automation | CloudWatch, SNS, EventBridge | Planned | - |
| 08 | CI/CD and Containers Capstone | ECR, ECS, GitHub Actions | Planned | - |

## How Each Project Is Documented

Every project folder keeps the plan and the actual build separate:

- **blueprint.md** is the plan I wrote and got reviewed before building anything.
- **implementation-log.md** is what actually happened: steps, errors, fixes, and test results.
- **README.md** is the final writeup, including mistakes I made and what I'd change.

Where the build ended up different from the plan, the blueprint's Design Change Log explains why.

## Security and Cost Practices

- No credentials, access keys, or secrets are committed to this repo.
- Account IDs, ARNs, IPs, and emails are redacted from screenshots and logs (replaced with `<ACCOUNT_ID>` or `123456789012`).
- Every project has a cost estimate before building and a cleanup plan after, and I check billing after teardown to confirm nothing is left running.

## Certifications

- AWS re/Start Graduate ([Credly badge](https://www.credly.com/badges/4d44a6aa-4365-4302-a7b0-260e2fd8efc4))
- AWS Certified Cloud Practitioner (exam scheduled December 2026)

## Contact

- LinkedIn: [linkedin.com/in/karl-san-jose](https://www.linkedin.com/in/karl-san-jose)