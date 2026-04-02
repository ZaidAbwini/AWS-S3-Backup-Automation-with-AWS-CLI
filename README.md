# AWS-S3-Backup-Automation-with-AWS-CLI
🧭 Overview
This project demonstrates how to automate secure file backups to Amazon S3 using the AWS CLI and Bash scripting. It walks through configuring the AWS CLI, creating and verifying S3 buckets, writing a script to upload files and validate results, and cleaning up resources to avoid costs.

The lab simulates a real-world use case where files from an on-premises environment need to be securely and repeatedly backed up to cloud storage — a common scenario in cloud, DevOps, and cybersecurity roles.

🎯 Project Objectives
✅ Configure AWS CLI on a local machine using access credentials
✅ Create and verify secure S3 buckets via the CLI
✅ Write a Bash script that automates:
Checking bucket permissions (ACL)
Uploading local files to S3
Logging results to a report
Verifying file existence in the cloud
✅ Understand and interpret S3 bucket ACLs and policies
✅ Test public access to files
✅ Delete cloud and local resources to avoid charges and demonstrate good cloud hygiene
🛠️ Tools & Technologies Used
AWS CLI (v2)
Amazon S3
Bash scripting
Git Bash (for Unix-like terminal on Windows)
PowerShell or Terminal
Optional: AWS Console for verification
🚀 Step-by-Step Walkthrough
🛠️ Step 1: Install AWS CLI
✅ 1. Download the AWS CLI v2 for Windows:
https://awscli.amazonaws.com/AWSCLIV2.msi

1 AWS CLI ✅ 2. Run the installer and follow the prompts to complete installation.

2 AWS CLI FINISH SETUP

✅ 3. Verify installation in the terminal: aws --version 3 AWS CLI DOWNLOAD CONFIRM

🚀 Step 2: Configure AWS CLI Credentials
Once the AWS CLI is installed, configure it with your AWS account credentials so you can manage resources from the command line.

✅1. Open Your Terminal
On Windows: Open Command Prompt, PowerShell, or Windows Terminal.
On Mac: Open Terminal.
On Linux: Open your preferred terminal app.
✅2. Run the Configuration Command
Type: aws configure 4 AWS CLI CONFIGURE You will need your

-Access key ID -Secret Access key -Default region -Default output format

When you run "aws configure", your credentials and settings are saved to:

Windows: C:\Users<YourUsername>.aws\credentials You can view the contents with powershell
$HOME.aws\credentials ⚠️ Important: These credentials are saved in plain text. Never upload this file to GitHub. Use .gitignore to exclude it if needed.

📦 Step 3: S3 Bucket Creation
To create the S3 bucket for file backups, use the AWS CLI: aws s3 mb s3://jarvis-s3-backup-lab-2025 5 AWS s3 Bucket creation We can confirm the bucket was created by running s3 ls 6 CONFIRM S3 BUCKET WAS CREATED

📁 Step 4: Create Local Files to Upload
To simulate a real backup scenario, we'll create a directory with a couple of test files. These will later be uploaded to the S3 bucket.

✅ 1. Create a Local Backup Directory
Open your terminal (PowerShell or Command Prompt) and run: mkdir files-to-backup

✅ 2. Create Sample Files in That Directory Use these commands to add content to the files:

bash echo Sample content for File 1 > files-to-backup/file1.txt echo Sample content for File 2 > files-to-backup/file2.txt These simulate basic logs, config files, or document backups

7 MKDIR SAMPLE CONTENT

🧾 Step 5: Create & Run S3 Backup Script
This step creates a Bash script that automates:

Verifying if the S3 bucket is public or private
Uploading files from the files-to-backup folder
Verifying uploads
Writing a report to upload_report.txt 7Create script in notepad 8 Save script After saving our script we will need to change the permissions to make it executable. 9 Chmod and run script
🚀 Step 6: Verify Output
After running the script with:./s3_backup.sh

You should see terminal output indicating the script has executed successfully, followed by the creation of a file named: upload_report.txt

This file contains:

✅ The current ACL (Access Control List) status of the S3 bucket

✅ A log of each uploaded file (including the source and destination)

✅ A verification list showing the uploaded files in the S3 bucket 10 script ran successfuly  output file

🔍 Step 7: Validate in AWS Console & Test Public Access
After running the backup script and generating upload_report.txt, use these steps to manually verify the files in AWS and test access behavior. ✅ 1. List Files in Your S3 Bucket

To confirm the files are really there: aws s3 ls s3://jarvis-s3-backup-lab-2025 11 confirm files were uploaded via cli

✅ 2. Check Bucket ACL (Access Control List) Use the following command to review the permissions assigned to your S3 bucket: aws s3api get-bucket-acl --bucket jarvis-s3-backup-lab-2025

12 s3 access = private

This command returns the Access Control List (ACL), which includes:

✅The bucket owner

✅Any grants given to other users or groups

✅Whether the bucket is private or public

🧹 Step 8: Clean Up AWS Resources
To avoid unwanted charges and keep our AWS environment clean, we will delete the resources you created during this lab. ✅ 1. Delete the Files From the S3 Bucket

This command will remove all files you uploaded: aws s3 rm s3://jarvis-s3-backup-2025 --recursive

✅2. After removing the files time to delete the bucket: aws s3 rb s3://jarvis-s3-backup-2025

14 remove files and bucket- cleanup

🧾 Step 9: Final Summary
This project demonstrates the automation of secure file backups to Amazon S3 using Bash and the AWS CLI.

🧠 What I Learned
How to install and configure AWS CLI on Windows
How to create and manage S3 buckets using the CLI
How to automate cloud operations with Bash scripting
How to verify security settings (ACL & bucket policy)
How to validate file uploads via CLI and browser
How to responsibly clean up cloud resources to avoid charges
