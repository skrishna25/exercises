# SSRF Lab: Spot the Obfuscation

Welcome to a simulated **Server-Side Request Forgery (SSRF)** lab environment, designed for cloud security enthusiasts, researchers, and students. This lab showcases how attackers might exploit SSRF vulnerabilities in cloud-native environments and how small mistakes in input validation can lead to big cloud exposures.

>  This project is for **educational purposes only**. All activity must remain within the boundaries of your local or lab environment.

---

## What is SSRF?

**SSRF (Server-Side Request Forgery)** is a vulnerability that allows an attacker to make the server issue HTTP requests to arbitrary destinations — including internal services that are otherwise inaccessible from the internet.

In cloud environments like AWS, GCP, and Azure, SSRF is particularly dangerous because it can be used to:

- Access **cloud metadata services**
- Steal **temporary IAM credentials**
- Move laterally or escalate privileges

---

##  Lab Objective

This lab challenges you to:

- Interact with a web UI that includes an SSRF-prone input
- Bypass SSRF filters using **creative obfuscation**
- Attempt to access sensitive internal metadata in a **controlled** and **logged** environment
- Learn how detection and prevention mechanisms work

There are multiple paths to success. Not all IPs look like IPs — can you find one that slips through?

Once you findout client_id, Secret and token 

##  Configure AWS CLI

```bash
aws configure
```
You'll be prompted to enter:

- **AWS Access Key ID**
- **AWS Secret Access Key**
- **Default region name** (e.g., `us-east-1`)
- **Default output format** (e.g., `json`)

Now you try validating whether tokens are configured correctly 
```bash
aws sts get-session-token
```
# AWS CLI Reconnaissance Cheat Sheet

This guide provides common **AWS CLI** commands used during cloud reconnaissance activities. Use these commands to enumerate IAM roles, EC2 instances, S3 buckets, and other resources.

## IAM Enumeration

```bash
# List IAM users
aws iam list-users

# List IAM roles
aws iam list-roles

# List IAM groups
aws iam list-groups

# List IAM policies
aws iam list-policies --scope Local

# Get current caller identity (whoami equivalent)
aws sts get-caller-identity

# Get IAM user details
aws iam get-user

# List attached policies for a user
aws iam list-attached-user-policies --user-name <username>

# Get inline policies for a user
aws iam list-user-policies --user-name <username>

# Enumerate group membership
aws iam list-groups-for-user --user-name <username>
```

## s3 Bucket
# List all accessible buckets
aws s3 ls

# List contents of a specific bucket
aws s3 ls s3://<bucket-name>

# Try downloading a file from an S3 bucket
aws s3 cp s3://<bucket-name>/<file> .

# Sync the entire bucket locally
aws s3 sync s3://<bucket-name> ./local-folder
```


