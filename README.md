# 🧭 S3 Backup Automation Lab

## 📑 Table of Contents

* [Overview](#overview)
* [Project Objectives](#project-objectives)
* [Tools & Technologies Used](#tools--technologies-used)
* [Step 1: Install AWS CLI](#step-1-install-aws-cli)
* [Step 2: Configure AWS CLI Credentials](#step-2-configure-aws-cli-credentials)
* [Step 3: S3 Bucket Creation](#step-3-s3-bucket-creation)
* [Step 4: Create Local Files to Upload](#step-4-create-local-files-to-upload)
* [Step 5: Create & Run S3 Backup Script](#step-5-create--run-s3-backup-script)
* [Step 6: Verify Output](#step-6-verify-output)
* [Step 7: Validate in AWS Console & Test Public Access](#step-7-validate-in-aws-console--test-public-access)
* [Step 8: Clean Up AWS Resources](#step-8-clean-up-aws-resources)
* [Step 9: Final Summary](#step-9-final-summary)

---

## 🧭 Overview

This project demonstrates how to automate secure file backups to Amazon S3 using the AWS CLI and Bash scripting.

It walks through:

* Configuring AWS CLI
* Creating and verifying S3 buckets
* Writing a script to upload files
* Validating results
* Cleaning up resources

This simulates a real-world backup scenario used in cloud, DevOps, and cybersecurity roles.

---

## 🎯 Project Objectives

* ✅ Configure AWS CLI using credentials
* ✅ Create and verify secure S3 buckets
* ✅ Automate file uploads with Bash
* ✅ Understand S3 ACLs and permissions
* ✅ Validate uploads
* ✅ Clean up resources

---

## 🛠️ Tools & Technologies Used

* AWS CLI (v2)
* Amazon S3
* Bash scripting
* Git Bash / PowerShell / Terminal

---

## 🚀 Step 1: Install AWS CLI

1. Download AWS CLI v2:
   https://awscli.amazonaws.com/AWSCLIV2.msi
<img width="1389" height="979" alt="download_CLI" src="https://github.com/user-attachments/assets/96cff55d-7d5c-46a5-9ff1-108e34a5d77e" />

2. Run installer and follow prompts
<img width="489" height="379" alt="installation_complete" src="https://github.com/user-attachments/assets/c2af5c84-6b4f-4e05-b6fa-52bcd4b530bf" />

3. Verify installation:
<img width="1105" height="618" alt="Verfiy_installation" src="https://github.com/user-attachments/assets/f251f2c2-1240-4644-a258-36dd2558f4c3" />

```bash
aws --version
```

---

## 🚀 Step 2: Configure AWS CLI Credentials

Run:

```bash
aws configure
```

Enter:

* Access Key ID
* Secret Access Key
* Default region
* Output format

⚠️ Credentials stored in:

```
C:\Users\<your-user>\.aws\credentials
```

⚠️ Never upload this file to GitHub.

---

## 📦 Step 3: S3 Bucket Creation

Create bucket:

```bash
aws s3 mb s3://jarvis-s3-backup-lab-2025
```

Verify:

```bash
aws s3 ls
```

---

## 📁 Step 4: Create Local Files to Upload

Create directory:

```bash
mkdir files-to-backup
```

Create sample files:

```bash
echo Sample content for File 1 > files-to-backup/file1.txt
echo Sample content for File 2 > files-to-backup/file2.txt
```

---

## 🧾 Step 5: Create & Run S3 Backup Script

This script will:

* Check bucket ACL
* Upload files
* Verify uploads
* Generate report

Make executable:

```bash
chmod +x s3_backup.sh
```

Run script:

```bash
./s3_backup.sh
```

---

## 🚀 Step 6: Verify Output

After running the script, you should see:

* Terminal success output
* File created: `upload_report.txt`

This file contains:

* ✅ Bucket ACL status
* ✅ Upload logs
* ✅ Verification of uploaded files

---

## 🔍 Step 7: Validate in AWS Console & Test Public Access

List uploaded files:

```bash
aws s3 ls s3://jarvis-s3-backup-lab-2025
```

Check bucket ACL:

```bash
aws s3api get-bucket-acl --bucket jarvis-s3-backup-lab-2025
```

---

## 🧹 Step 8: Clean Up AWS Resources

Delete all files:

```bash
aws s3 rm s3://jarvis-s3-backup-2025 --recursive
```

Delete bucket:

```bash
aws s3 rb s3://jarvis-s3-backup-2025
```

---

## 🧾 Step 9: Final Summary

### 🧠 What I Learned

* How to install and configure AWS CLI
* How to create and manage S3 buckets
* How to automate backups using Bash scripting
* How to verify ACLs and security settings
* How to validate uploads via CLI
* Importance of cleaning up cloud resources to avoid costs
