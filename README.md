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

<img width="1102" height="442" alt="Access_Key" src="https://github.com/user-attachments/assets/fb41b97a-a227-4042-bef2-064145da7acd" />
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
aws s3 mb s3://zaid-s3-backup-lab-2026
```
<img width="1099" height="111" alt="Create_s3_bucket" src="https://github.com/user-attachments/assets/219ae53f-301f-422b-8a51-de5c54812e9b" />

Verify:

```bash
aws s3 ls
```
<img width="1100" height="98" alt="Verifiy_S3Bucket" src="https://github.com/user-attachments/assets/911c3abe-edb4-4cee-9afd-d5680a2c71fb" />

---

## 📁 Step 4: Create Local Files to Upload

Create directory:

```bash
mkdir files-to-backup
```
<img width="991" height="100" alt="Echo" src="https://github.com/user-attachments/assets/11ee579d-260b-4c39-9a19-a4c01444d2fc" />

Create sample files:

```bash
echo Sample content for File 1 > files-to-backup/file1.txt
echo Sample content for File 2 > files-to-backup/file2.txt
```
<img width="589" height="215" alt="Echo1" src="https://github.com/user-attachments/assets/9bc56b74-58e3-434c-be45-025d368cfd92" />
<img width="646" height="140" alt="Echo2" src="https://github.com/user-attachments/assets/a995058a-50ee-4e4f-9afa-af1bc92b2169" />

---

## 🧾 Step 5: Create & Run S3 Backup Script

This script will:

* Check bucket ACL
* Upload files
* Verify uploads
* Generate report
<img width="992" height="533" alt="Script1" src="https://github.com/user-attachments/assets/11d17a0d-d194-4be1-bc5a-e3ef691efe01" />

Make executable:
You must download Git Bash for windows in order to run the script
<img width="480" height="107" alt="Bash" src="https://github.com/user-attachments/assets/f634ba59-c370-4f67-8550-998e64ed80d1" />

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
<img width="1037" height="594" alt="Output" src="https://github.com/user-attachments/assets/09ff3e86-8de1-406d-8c40-5e32219b75bd" />

---

## 🔍 Step 7: Validate in AWS Console & Test Public Access

List uploaded files:
<img width="1105" height="618" alt="Verfiy_installation" src="https://github.com/user-attachments/assets/5566144e-5a6d-4d99-bd08-ec60ad857a91" />

```bash
aws s3 ls s3://zaid-s3-backup-lab-2026
```

Check bucket ACL:
<img width="892" height="296" alt="verfiy it exists" src="https://github.com/user-attachments/assets/a9f3dc62-01e4-4cda-9817-56703bfa6967" />

```bash
aws s3api get-bucket-acl --bucket zaid-s3-backup-lab-2026
```

---

## 🧹 Step 8: Clean Up AWS Resources

Delete all files:
<img width="935" height="140" alt="verify removal" src="https://github.com/user-attachments/assets/b167a6f2-be66-4ee7-93e4-d4d22341b706" />

```bash
aws s3 rm s3://zaid-s3-backup-2026 --recursive
```

Delete bucket:

```bash
aws s3 rb s3://zaid-s3-backup-2026
```
Verfiy Bucket is deleted:

<img width="752" height="67" alt="confirm removal 1" src="https://github.com/user-attachments/assets/9c2ed705-96aa-4fa6-be1d-2815273032ef" />

```bash
aws s3 ls
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
