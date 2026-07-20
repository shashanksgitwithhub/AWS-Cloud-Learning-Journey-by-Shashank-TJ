<p align="center">
  <img src="https://img.shields.io/badge/AWS-S3-green" alt="AWS Badge">
</p>

# ☁ Day 15 - Amazon Simple Storage Service (Amazon S3)

## Objective

To understand Amazon S3, learn how to create and manage S3 buckets, upload objects, and explore storage classes and bucket security.

---

# What is Amazon S3?

Amazon Simple Storage Service (Amazon S3) is an object storage service that provides scalable, durable, and highly available storage for files, images, videos, backups, logs, and application data.

Amazon S3 is designed to store and retrieve any amount of data from anywhere over the internet.

---

# Why Do We Need Amazon S3?

Amazon S3 is used for:

* File Storage
* Website Hosting
* Data Backup
* Disaster Recovery
* Log Storage
* Media Storage
* Application Data
* Data Archiving

---

# Features of Amazon S3

* Unlimited object storage
* High durability (99.999999999%)
* High availability
* Multiple storage classes
* Versioning
* Lifecycle management
* Encryption
* Access control using Bucket Policies and IAM

---

# What is an S3 Bucket?

A Bucket is a logical container used to store objects in Amazon S3.

Every bucket name must be:

* Globally unique
* DNS compliant
* Lowercase

Example:

```text id="jczrm8"
shashank-aws-learning-bucket
```

---

# What is an Object?

An Object is a file stored inside an S3 bucket.

Every object consists of:

* File
* Metadata
* Object Key (File Name)

Examples:

* image.png
* notes.pdf
* backup.zip

---

# Amazon S3 Storage Classes

## 1. S3 Standard

* Frequently accessed data
* High availability
* Low latency

---

## 2. S3 Intelligent-Tiering

Automatically moves data between storage tiers based on usage.

---

## 3. S3 Standard-IA

Used for infrequently accessed data.

---

## 4. S3 One Zone-IA

Stores data in a single Availability Zone at a lower cost.

---

## 5. S3 Glacier Instant Retrieval

For archive data that requires quick access.

---

## 6. S3 Glacier Flexible Retrieval

Low-cost archival storage with retrieval times ranging from minutes to hours.

---

## 7. S3 Glacier Deep Archive

Lowest-cost storage for long-term archival data.

---

# Amazon S3 Architecture

<img width="641" height="361" alt="S3 drawio" src="https://github.com/user-attachments/assets/d909a977-2ace-4427-8efd-2964899f71f9" />

---

# Practical Performed

## Step 1: Create an S3 Bucket

Navigate to:

AWS Console → S3

Click:

Create Bucket

Configuration:

* Bucket Name - my-bucket
* AWS Region
* Block Public Access (Default Enabled)

Click:

Create Bucket

---

## Step 2: Upload Objects

Open the bucket.

Click:

Upload

Select files from the local system.

Click:

Upload -- Verify uploaded files inside the bucket.

---

## Step 3: Give Permissions to the bucket

Edit Block public access (bucket settings).

☐ Uncheck - Block all public access

Save changes 

---

## Step 4: Edit bucket policy

Bucket policy: 

```
Policy
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowOnlyMyLaptop",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::my-bucket-470829880485-ap-south-2-an/sunflower.jpeg"
        }
    ]
}
```


## Step 5: View Object

Example:

* sunflower.jpeg
  
---

## Step 6: Download Objects

Select an object.

Click:

Download

Verify the file downloads successfully.

Because the policy is given as - "Action": "s3:GetObject"

```
This means you can read and download the image.
```

---

## Step 7: Delete Object (optional)

Select an object.

Click:

Delete

Confirm deletion.

---

# Practical Outcome

✅ Created an S3 Bucket.

✅ Uploaded files.

✅ Given permissions.

✅ Added Bucket policy.

✅ Downloaded files.

✅ Deleted objects.

---

# Bucket Security

Amazon S3 security can be managed using:

* IAM Policies
* Bucket Policies
* Access Control Lists (ACLs)
* Block Public Access

Best Practice:

Keep Block Public Access enabled unless public access is specifically required.

---

# Advantages of Amazon S3

* Highly durable
* Scalable
* Secure
* Cost-effective
* Easy integration with AWS services
* Supports static website hosting

---

# Key Learnings

* Learned the purpose of Amazon S3.
* Created an S3 bucket.
* Uploaded and managed objects.
* Understood storage classes.
* Learned S3 security best practices.

---

# Interview Questions

### What is Amazon S3?

Amazon S3 is an object storage service used to store and retrieve data over the internet.

---

### What is an S3 Bucket?

A Bucket is a container used to store objects in Amazon S3.

---

### What is an Object?

An Object is a file stored inside an S3 bucket.

---

### What is the difference between Amazon S3 and Amazon EBS?

| Amazon S3                  | Amazon EBS                |
| -------------------------- | ------------------------- |
| Object Storage             | Block Storage             |
| Stores Files               | Stores Disk Volumes       |
| Accessible over HTTP/HTTPS | Attached to EC2 Instances |
| Unlimited Storage          | Fixed Volume Size         |

---

### Can an S3 Bucket have the same name as another bucket?

No.

Bucket names must be globally unique.

---

### Which storage class is best for long-term archival?

Amazon S3 Glacier Deep Archive.

---

# Screenshots

* Amazon S3 Dashboard<img width="1907" height="1009" alt="Screenshot 2026-07-20 220750" src="https://github.com/user-attachments/assets/b523f075-f76b-4246-aa37-0fc46162ef92" />

* Bucket Creation<img width="1907" height="1008" alt="Screenshot 2026-07-20 221049" src="https://github.com/user-attachments/assets/b9d7fb1a-fbac-4599-b254-67393d15b53e" />
  <img width="1907" height="1011" alt="Screenshot 2026-07-20 221059" src="https://github.com/user-attachments/assets/00116f7f-5155-4396-9b29-267a23b65099" />
  <img width="1907" height="1014" alt="Screenshot 2026-07-20 221107" src="https://github.com/user-attachments/assets/d80602b4-bc63-4a8c-a28b-18c230ec1072" />

* Bucket Details<img width="1907" height="1011" alt="Screenshot 2026-07-20 221600" src="https://github.com/user-attachments/assets/d502929f-2149-4f99-b9cb-5b76f0062a82" />

* Upload Objects<img width="1907" height="1010" alt="Screenshot 2026-07-20 222117" src="https://github.com/user-attachments/assets/fff5d533-34cb-472d-b65a-502bcbafa152" />

* Uploaded Files<img width="1907" height="1011" alt="Screenshot 2026-07-20 222132" src="https://github.com/user-attachments/assets/c3f1b076-3238-4639-a0cb-c8b076ce83ea" />
  <img width="1907" height="1011" alt="Screenshot 2026-07-20 222207" src="https://github.com/user-attachments/assets/67496eb3-7dd3-4258-b39a-c5c16aeb3a8e" />
  <img width="1907" height="1009" alt="Screenshot 2026-07-20 235457" src="https://github.com/user-attachments/assets/f182b5d4-cd54-4876-b42f-068120a3c77c" />

* Bucket Permissions<img width="1907" height="1012" alt="Screenshot 2026-07-20 222322" src="https://github.com/user-attachments/assets/b14c8c36-530e-4cec-8baf-df76c1fce6bc" />
  <img width="1907" height="1008" alt="Screenshot 2026-07-20 222333" src="https://github.com/user-attachments/assets/483054d5-eeb2-4ad7-b285-db2dea0d08ee" />
  <img width="1907" height="1008" alt="Screenshot 2026-07-20 222341" src="https://github.com/user-attachments/assets/aa614f00-04c0-477b-a3fd-1a86d755199e" />
  <img width="1907" height="1012" alt="Screenshot 2026-07-20 222357" src="https://github.com/user-attachments/assets/d7b37a61-5770-48a4-a84a-fc5c4b79a03f" />

* Edit Bucket policy<img width="1907" height="1009" alt="Screenshot 2026-07-20 222958" src="https://github.com/user-attachments/assets/8aada314-3845-4589-9f02-fc4ee1f158cd" />
  <img width="1907" height="1013" alt="Screenshot 2026-07-20 223132" src="https://github.com/user-attachments/assets/e3bc4b63-80fe-4217-952d-f546b0d752b3" />
  <img width="1907" height="1009" alt="Screenshot 2026-07-20 223304" src="https://github.com/user-attachments/assets/ce5cb75c-04db-463f-9aae-aaa67e277450" />
  <img width="1907" height="1011" alt="Screenshot 2026-07-20 223324" src="https://github.com/user-attachments/assets/40f451e7-3a06-4fe1-ac53-9c7006341d8f" />

* View Object<img width="1907" height="1010" alt="Screenshot 2026-07-20 223350" src="https://github.com/user-attachments/assets/57267a1f-2929-4ef3-a4d4-4f21cad0da9d" />

---

# Conclusion

Successfully created an Amazon S3 bucket, uploaded objects and given permissions, created bucket policy and managed objects, and learned how Amazon S3 provides scalable, secure, and highly durable object storage for cloud applications.
