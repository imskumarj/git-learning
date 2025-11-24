
# AWS (Beginner Guide)

This document provides a concise, beginner-friendly introduction to Amazon Web Services (AWS). It covers core concepts, account and CLI setup, common services and example commands you can run from PowerShell on Windows, plus basic security and cost-management tips.

## What is AWS?

AWS is a broad set of cloud services offered by Amazon for computing, storage, networking, databases, analytics, machine learning, and more. Instead of owning hardware, you provision resources on-demand and pay for what you use.

## Core services (high-level)

- **EC2 (Elastic Compute Cloud):** Virtual machines (servers) in the cloud.
- **S3 (Simple Storage Service):** Object storage for files, backups, and static assets.
- **RDS / DynamoDB:** Managed relational databases (RDS) and NoSQL (DynamoDB).
- **Lambda:** Serverless functions that run code in response to events.
- **VPC:** Virtual network where you place your resources.
- **IAM:** Identity and Access Management — users, roles, and permissions.

## Create an AWS account & basic safety

- Sign up at https://aws.amazon.com/. Use a real email and a secure password.
- Do not use the root account for everyday tasks. Create an IAM user with limited privileges and enable MFA for the root account and IAM users that need it.

## Install and configure the AWS CLI (Windows / PowerShell)

1. Install the AWS CLI v2 by downloading the MSI from https://aws.amazon.com/cli/ or using a package manager such as `winget` or `chocolatey`.

	 Example (if you have `winget`):

	 ```powershell
	 winget install --id=Amazon.AWSCLI
	 aws --version
	 ```

2. Configure the CLI with your credentials (use an IAM user with programmatic access):

	 ```powershell
	 aws configure
	 # Enter AWS Access Key ID
	 # Enter AWS Secret Access Key
	 # Default region name (e.g. us-east-1)
	 # Default output format (e.g. json)
	 ```

	 Tip: For scripts and CI, use named profiles or environment variables instead of embedding keys in code.

## Basic example commands (PowerShell)

- S3 - list buckets and upload a file:

	```powershell
	aws s3 ls
	aws s3 mb s3://my-unique-bucket-name-12345 --region us-east-1
	aws s3 cp .\example.txt s3://my-unique-bucket-name-12345/
	aws s3 ls s3://my-unique-bucket-name-12345
	```

- EC2 - describe instances:

	```powershell
	aws ec2 describe-instances --region us-east-1
	```

- Lambda - list functions:

	```powershell
	aws lambda list-functions --region us-east-1
	```

- IAM - list users (requires appropriate permissions):

	```powershell
	aws iam list-users
	```

## Quick tutorial ideas for practice

- Create an S3 bucket and host a simple static website.
- Launch an EC2 instance, SSH into it (or use Session Manager) and run a web server.
- Create a Lambda function triggered by S3 object uploads.
- Use CloudWatch to view logs and create a simple alarm.

## Security & best practices (beginner)

- Use IAM users and roles — follow the principle of least privilege.
- Enable Multi-Factor Authentication (MFA) for privileged accounts.
- Never commit AWS access keys to source control. Use environment variables, secrets managers, or IAM roles for EC2/Actions.
- Enable billing alerts and review your bills regularly.

## Cost management tips

- Understand the Free Tier limits and monitor usage while learning.
- Tag resources (e.g., `project`, `owner`) to track costs.
- Use the AWS Cost Explorer and Budgets to set alerts when spending exceeds thresholds.

## Where to learn next

- AWS official tutorials: https://aws.amazon.com/getting-started/
- Free Tier labs: practice with free-tier eligible resources.
- AWS documentation and service guides: https://docs.aws.amazon.com/

---

If you want, I can also:
- add step-by-step hands-on labs to this file (S3 website, EC2 webserver, Lambda trigger),
- create a small sample repo with scripts and `cloud-README` examples, or
- commit this change and push it to the repository.
