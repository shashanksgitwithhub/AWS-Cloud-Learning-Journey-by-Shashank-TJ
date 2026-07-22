<p align="center">
  <img src="https://img.shields.io/badge/AWS-CLI-orange" alt="AWS Badge">
</p>

# ☁ Day 16 - Amazon S3 using AWS CLI

## Objective

To learn how to manage Amazon S3 resources using the AWS Command Line Interface (AWS CLI).

---

# What is AWS CLI?

AWS Command Line Interface (AWS CLI) is a tool that allows users to interact with AWS services using terminal commands instead of the AWS Management Console.

Benefits:

* Automation
* Faster administration
* Scripting
* Infrastructure management

---

# Prerequisites

* AWS CLI Installed
* AWS Account
* IAM User with Programmatic Access
* Access Key ID
* Secret Access Key

---

# Practical Performed

## Step 1: Verify Installation

```bash
aws --version
```

---

## Step 2: Configure AWS CLI

```bash
aws configure
```

Provide:

* AWS Access Key ID
* AWS Secret Access Key
* Region (Example: ap-south-1)
* Output Format (json)

---

## Step 3: List Buckets

```bash
aws s3 ls
```

---

## Step 4: Create Bucket

```bash
aws s3 mb s3://your-bucket-name
```

---

## Step 5: Upload File

```bash
aws s3 cp sample.txt s3://your-bucket-name
```

---

## Step 6: List Objects

```bash
aws s3 ls s3://your-bucket-name
```

---

## Step 7: Delete Object

```bash
aws s3 rm s3://your-bucket-name/sample.txt
```

---

## Step 8: Delete Bucket

```bash
aws s3 rb s3://your-bucket-name
```

---

# Practical Outcome

✅ Configured AWS CLI.

✅ Created an S3 Bucket.

✅ Uploaded Objects.

✅ Deleted Objects.

---

# Key Learnings

* AWS CLI configuration
* Managing S3 through commands
* Authentication using IAM Access Keys
* Command-line administration

---

# Interview Questions

### What is AWS CLI?

AWS CLI is a command-line tool used to manage AWS resources.

---

### Which command lists S3 buckets?

```bash
aws s3 ls
```

---

### Which command uploads a file?

```bash
aws s3 cp file.txt s3://bucket-name
```

---

### Screenshots

* Create IAM User and add persmission options<img width="1905" height="1006" alt="Screenshot 2026-07-22 224429" src="https://github.com/user-attachments/assets/c52bb236-130a-4daa-a538-0c441e0de5bb" />
  <img width="1907" height="1013" alt="Screenshot 2026-07-22 224450" src="https://github.com/user-attachments/assets/9dd95d85-3024-4e41-be0b-52abc617dee7" />
  <img width="1907" height="1013" alt="Screenshot 2026-07-22 224502" src="https://github.com/user-attachments/assets/5a2d8072-07ba-4f85-a0ac-47661de2d5df" />
  <img width="1907" height="1009" alt="Screenshot 2026-07-22 224523" src="https://github.com/user-attachments/assets/2199cae0-ba90-420f-99c0-f71fe430d999" />
* Create Access key<img width="1907" height="1011" alt="Screenshot 2026-07-22 224549" src="https://github.com/user-attachments/assets/e65c7bff-9dd2-4939-bda2-b53f113bcd3b" />
  <img width="1907" height="1008" alt="Screenshot 2026-07-22 224610" src="https://github.com/user-attachments/assets/5413f406-e342-45a3-9750-73e80e0e989f" />
  <img width="1906" height="1006" alt="Screenshot 2026-07-22 224648" src="https://github.com/user-attachments/assets/737d089e-45b9-4f2b-9d86-b1b54b6fb78b" />
  <img width="1907" height="1010" alt="Screenshot 2026-07-22 224814" src="https://github.com/user-attachments/assets/21da2acf-8f61-46a1-b7bc-7ffc1feaea11" />
* Aws version, Aws configure<img width="1907" height="316" alt="Screenshot 2026-07-22 225748" src="https://github.com/user-attachments/assets/ae41a333-cce3-407a-ad81-5f5785bbd3e7" />
* Create a bucket<img width="1907" height="326" alt="Screenshot 2026-07-22 225748" src="https://github.com/user-attachments/assets/df66a9cf-d6e1-4202-a40b-eb273af7eaf6" />
  <img width="1907" height="1008" alt="Screenshot 2026-07-22 225820" src="https://github.com/user-attachments/assets/5c2005c4-df24-40e9-a271-431c213f2efd" />
* Upload File<img width="1907" height="1008" alt="Screenshot 2026-07-22 233223" src="https://github.com/user-attachments/assets/c6628165-ae4f-4833-82f8-853396cea7d1" />
  <img width="1907" height="1011" alt="Screenshot 2026-07-22 233834" src="https://github.com/user-attachments/assets/1136e1c2-fd34-42e5-a99a-6b34b3ee10a8" />
* Delete Object<img width="1907" height="206" alt="Screenshot 2026-07-22 234000" src="https://github.com/user-attachments/assets/e9645f9e-c845-402c-be44-c15e32a5b19d" />
  <img width="1903" height="1005" alt="Screenshot 2026-07-22 234009" src="https://github.com/user-attachments/assets/8b25a2a2-bad7-4753-a423-34d63ce19a87" />
* Delete Bucket<img width="1907" height="203" alt="Screenshot 2026-07-22 234134" src="https://github.com/user-attachments/assets/b2e60ebc-f4fa-43ff-ae16-b9526e30bdf4" />
  <img width="1907" height="1012" alt="Screenshot 2026-07-22 234103" src="https://github.com/user-attachments/assets/1520f544-954a-4ac4-a638-47cbf8f4c110" />
  
---

# Conclusion

Successfully managed Amazon S3 resources using AWS CLI and learned how command-line tools simplify AWS administration and automation.
