Welcome to a Server-Side Request Forgery (SSRF) simulation designed for safe and responsible security learning. This lab demonstrates how attackers might abuse SSRF vulnerabilities in misconfigured cloud applications — particularly when internal metadata services are not properly protected.

⚠️ For educational use only. Do not use these techniques on real systems without explicit permission.

🔍 What is SSRF?
Server-Side Request Forgery (SSRF) occurs when a server-side application fetches remote resources based on untrusted user input. This can lead to:

Accessing internal services

Reading cloud metadata endpoints

Leveraging IP interpretation quirks

🎯 Challenge Goals
Understand SSRF risks in cloud-native apps

Interact with the vulnerable input field

Explore how different URL formats behave

Discover how encoding and numeric representations affect filters

🚧 SSRF Filter Behavior
Requests to well-known internal IPs (e.g., 169.254.169.254) are blocked

However, not all numeric IPs look like IPs

Some encodings or conversions may evade simple filters

🧠 Can you find a safe way to represent a restricted IP?

☁️ AWS S3 Integration
This section allows you to simulate cloud exposure by uploading your app or SSRF artifacts to Amazon S3.

✅ Configure AWS CLI
bash
Copy
Edit
aws configure
You'll be prompted to enter:

Access Key ID

Secret Access Key

Default region (e.g., ap-south-1)

Output format (e.g., json)

📦 Create an S3 Bucket
bash
Copy
Edit
aws s3 mb s3://your-unique-bucket-name
📁 Upload Lab Files
bash
Copy
Edit
aws s3 cp . s3://your-unique-bucket-name/ssrf-lab/ --recursive
🌐 Make an Image Public (Optional)
bash
Copy
Edit
aws s3 cp ssrf.png s3://your-unique-bucket-name/ssrf-lab/ssrf.png --acl public-read
📘 Notes for GitHub
This project is safe for GitHub and educational platforms.

It does not contain active exploitation code or direct payloads.

Metadata access logic is handled on the backend with strict filters.

Obfuscation challenges are presented purely for learning how filters work.

🙋 Want More?
Add CloudTrail or IAM role tracing

Expand the app to simulate attacker movement after SSRF

Show how credentials obtained through SSRF can affect cloud resources

Let me know if you'd like a GitHub Acti
