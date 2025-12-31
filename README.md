# AWS Static Website Hosting on S3

## Overview
This project demonstrates how to host a static website using **Amazon S3 Static Website Hosting** with proper access control and security considerations.

The goal is not just to make a website live, but to understand:
- How S3 serves content over HTTP
- How public access is safely controlled
- How IAM and bucket policies work together
- When S3 static hosting is the correct architectural choice

This is a foundational AWS project and serves as an entry point into Cloud and DevOps engineering.

---

## Architecture
**High-level flow:**

User (Browser)  
→ Internet  
→ S3 Static Website Endpoint  
→ HTML / CSS / JS Files  

There are **no servers**, **no backend**, and **no databases** involved.

---

## Tech Stack
- **AWS S3** – Object storage & static website hosting
- **IAM** – Access control and permissions
- **HTML / CSS / JavaScript** – Static frontend content
- **AWS Management Console** – Resource configuration

---

## Prerequisites
- An active AWS account
- Basic understanding of AWS regions (example: `ap-south-1`)
- A static website containing at least:
  - `index.html`
  - (Optional) `error.html`

---

## Project Objective
- Host a publicly accessible static website on S3
- Allow **read-only public access**
- Prevent unauthorized uploads, deletions, or modifications
- Understand AWS security and permission boundaries

---

## Implementation Steps

### 1. Create an S3 Bucket
- Bucket name must be globally unique
- Select a region (example: `ap-south-1`)
- Disable ACLs (recommended)
- Keep default encryption enabled

---

### 2. Upload Website Files
Upload the static website files:
- `index.html`
- `error.html` (optional)
- CSS, JS, images (if any)

---

### 3. Enable Static Website Hosting
- Go to **Properties → Static website hosting**
- Enable static website hosting
- Set:
  - Index document: `index.html`
  - Error document: `error.html`

S3 generates a **website endpoint URL**.

---

### 4. Configure Public Access Settings
- Disable **Block all public access**
- Confirm acknowledgment

This step allows controlled public access through policies, not open permissions.

---

### 5. Apply Bucket Policy (Public Read Only)
Attach a bucket policy that:
- Allows **public read (`s3:GetObject`)**
- Does NOT allow write, delete, or list operations

Example policy:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::YOUR_BUCKET_NAME/*"
    }
  ]
}
```

---

## Security Validation

The following checks were performed to ensure the bucket is secure and correctly configured:

- Verified that objects are publicly accessible only via `s3:GetObject`
- Confirmed that public users cannot upload, modify, or delete objects
- Attempted access without proper permissions to ensure denial
- Ensured no IAM credentials are exposed in the frontend
- Confirmed the bucket does not allow directory listing

This validates that the bucket follows the **principle of least privilege** and is safe for hosting static public content.

## Cleanup
- Deleted all objects from the S3 bucket
- Deleted the S3 bucket after testing
- Verified no remaining AWS resources to avoid unnecessary cost
