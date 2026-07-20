<p align="center">
  <img src="https://img.shields.io/badge/AWS-IAM-red" alt="AWS Badge">
</p>

# ☁ Day 14 - AWS Identity and Access Management (IAM)

## Objective

To understand AWS Identity and Access Management (IAM) and learn how to create and manage IAM Users, Groups, Roles, and Policies to securely control access to AWS resources.

---

# What is IAM?

AWS Identity and Access Management (IAM) is a global AWS service that enables you to securely manage access to AWS services and resources.

IAM allows you to control:

* Who can access AWS resources.
* What actions they can perform.
* Which AWS services they can access.

IAM follows the principle of **Least Privilege**, granting users only the permissions required to perform their tasks.

---

# Why Do We Need IAM?

Without IAM:

* Everyone would require access to the AWS Root User.
* Increased security risks.
* Difficult to manage permissions.

With IAM:

* Secure user management.
* Fine-grained access control.
* Multi-user collaboration.
* Improved security.

---

# Components of IAM

## 1. Root User

The Root User is created automatically when an AWS account is created.

Characteristics:

* Full access to all AWS services.
* Cannot be restricted by IAM policies.
* Should only be used for account-level tasks.

**Best Practice:**

* Enable Multi-Factor Authentication (MFA).
* Avoid using the Root User for daily tasks.

---

## 2. IAM User

An IAM User represents an individual person or application that needs access to AWS.

Each IAM User has unique credentials:

* Username
* Password (Console Access)
* Access Key ID
* Secret Access Key (Programmatic Access)

---

## 3. IAM Group

An IAM Group is a collection of IAM Users.

Permissions assigned to the group are automatically inherited by all members.

Example:

Developers Group

* EC2 Access
* S3 Access

---

## 4. IAM Policy

A Policy is a JSON document that defines permissions.

Policies specify:

* Effect (Allow or Deny)
* Actions
* Resources

Example:

```json
{
  "Effect": "Allow",
  "Action": "s3:*",
  "Resource": "*"
}
```

---

## 5. IAM Role

An IAM Role is an identity that AWS services or users can assume temporarily.

Unlike IAM Users, Roles do not have permanent credentials.

Examples:

* EC2 accessing S3
* Lambda accessing DynamoDB
* CloudWatch accessing other AWS services

---

# IAM Architecture

<img width="561" height="561" alt="AdobeExpressPhotos_f8020a778c9549f28dae717a531e4267_CopyEdited" src="https://github.com/user-attachments/assets/4b8dd8be-ceec-44d5-a201-645853e56207" />

---

# Practical Performed

## Step 1: Create an IAM User

Navigate to:

AWS Console → IAM → Users

Click:

Create two User's

Configuration:

* User Name: DemoUser
* User Name: DemoUser1
* Console Access: Enabled

---

## Step 2: Set Permissions

Choose:

Add User's to Group

or

Attach Policies Directly

Example Policy:

AmazonEC2FullAccess

---

## Step 3: Create an IAM Group

Navigate to:

IAM → User Groups

Click:

Create Group

Example:

Developers

Attach Policy:

AmazonEC2FullAccess

Add IAM Users to the group.

---

## Step 4: Create an IAM Role

Navigate to:

IAM → Roles

Click:

Create Role

Trusted Entity:

AWS Service

Example:

EC2

Attach Policy:

AmazonS3ReadOnlyAccess

Create the role.

---

## Step 5: Test IAM Permissions

Login using the IAM User credentials and verify access based on assigned permissions.

---

# Practical Outcome

✅ Created IAM Users.

✅ Created IAM Groups.

✅ Attached IAM Policies.

✅ Created an IAM Role.

✅ Assigned permissions securely.

---

# Best Practices

* Use IAM Users instead of the Root User.
* Enable MFA for the Root User and IAM Users.
* Follow the Principle of Least Privilege.
* Rotate Access Keys regularly.
* Prefer IAM Roles over long-term access keys for AWS services.

---

# Key Learnings

* Understood IAM fundamentals.
* Learned the difference between Users, Groups, Roles, and Policies.
* Created IAM Users and Groups.
* Assigned permissions using Policies.
* Created IAM Roles for AWS services.

---

# Interview Questions

### What is IAM?

IAM is an AWS service used to securely manage authentication and authorization for AWS resources.

---

### What is the difference between an IAM User and an IAM Role?

| IAM User                     | IAM Role                                |
| ---------------------------- | --------------------------------------- |
| Permanent Identity           | Temporary Identity                      |
| Has Password and Access Keys | No Permanent Credentials                |
| Used by People               | Used by AWS Services or Temporary Users |

---

### What is an IAM Policy?

An IAM Policy is a JSON document that defines permissions for AWS resources.

---

### What is the Principle of Least Privilege?

Users should receive only the minimum permissions necessary to perform their tasks.

---

### Why should the Root User not be used daily?

Because it has unrestricted access to all AWS resources, increasing security risks.

---

### What is MFA?

Multi-Factor Authentication (MFA) provides an additional layer of security by requiring a second form of authentication besides the password.

---

# Screenshots

* IAM Dashboard<img width="1907" height="1008" alt="Screenshot 2026-07-20 115342" src="https://github.com/user-attachments/assets/93b15768-7e00-4992-8111-3823553e751a" />

* Create IAM User's<img width="1907" height="1009" alt="Screenshot 2026-07-20 112320" src="https://github.com/user-attachments/assets/ac0c769f-50ee-4d6d-be66-d3f00e2f611d" />
  <img width="1907" height="1014" alt="Screenshot 2026-07-20 112331" src="https://github.com/user-attachments/assets/037557c7-0c88-4bfd-97e0-be0780e38318" />
  <img width="1907" height="1014" alt="Screenshot 2026-07-20 112412" src="https://github.com/user-attachments/assets/1279f70f-019b-4a03-a3f2-ad158cecc7c2" />
  <img width="1907" height="1008" alt="Screenshot 2026-07-20 112423" src="https://github.com/user-attachments/assets/7b4d633a-ff91-4568-ae72-5a07f8e2a167" />
  <img width="1907" height="1008" alt="Screenshot 2026-07-20 112446" src="https://github.com/user-attachments/assets/46a9c12f-940e-4438-bfc6-e56a985204a6" />
  <img width="1907" height="1010" alt="Screenshot 2026-07-20 112612" src="https://github.com/user-attachments/assets/72883d17-a339-47e4-ab5c-cece1130ef54" />
  <img width="1907" height="1010" alt="Screenshot 2026-07-20 112856" src="https://github.com/user-attachments/assets/edbeb68f-ba20-4393-90c0-f7002307de3b" />
  <img width="1907" height="1010" alt="Screenshot 2026-07-20 112938" src="https://github.com/user-attachments/assets/05441561-ee05-42c5-81ab-a94379e80cbd" />
  <img width="1907" height="1016" alt="Screenshot 2026-07-20 112947" src="https://github.com/user-attachments/assets/273e0ef2-3851-4795-8bba-c53a02ca1e53" />
  <img width="1907" height="1012" alt="Screenshot 2026-07-20 113143" src="https://github.com/user-attachments/assets/4f9958d9-8d6f-46d0-963d-86112610618c" />

* IAM User Details<img width="1907" height="1013" alt="Screenshot 2026-07-20 112646" src="https://github.com/user-attachments/assets/3161ee71-23bd-412a-989b-a56274e22213" />
  <img width="1907" height="1014" alt="Screenshot 2026-07-20 115651" src="https://github.com/user-attachments/assets/650761a2-ca68-4f5a-8c5d-422e10dd16d6" />

* IAM User Group<img width="1907" height="1011" alt="Screenshot 2026-07-20 113205" src="https://github.com/user-attachments/assets/c572e0f8-ee03-4a2a-92c9-ce27825bdcce" />

* Attached Policies<img width="1907" height="1012" alt="Screenshot 2026-07-20 113340" src="https://github.com/user-attachments/assets/add6455b-71c9-4988-84f8-183e7e70bb33" />
  <img width="1907" height="1008" alt="Screenshot 2026-07-20 113354" src="https://github.com/user-attachments/assets/ee04ffa9-d4d4-4e1d-88a5-c011b9e8ad5b" />

* IAM Role Creation<img width="1907" height="1010" alt="Screenshot 2026-07-20 113545" src="https://github.com/user-attachments/assets/11c93314-6a16-49d7-9273-b689d4fc5d6a" />
  <img width="1907" height="1011" alt="Screenshot 2026-07-20 113555" src="https://github.com/user-attachments/assets/fc3d0a90-4de9-4adb-abfc-74570c42fb5c" />
  <img width="1907" height="1013" alt="Screenshot 2026-07-20 113618" src="https://github.com/user-attachments/assets/d98e00a0-840a-4410-944c-7c47624f62be" />
  <img width="1907" height="1010" alt="Screenshot 2026-07-20 113735" src="https://github.com/user-attachments/assets/8ddb60a0-b065-426a-8da7-34676f1d44ba" />
  <img width="1907" height="1006" alt="Screenshot 2026-07-20 113743" src="https://github.com/user-attachments/assets/bff5113b-d7a2-4bdf-885d-86f880ef3288" />
  <img width="1907" height="1007" alt="Screenshot 2026-07-20 113818" src="https://github.com/user-attachments/assets/92e2be1b-f884-4590-aaf5-4bbd99c05f95" />

* IAM Role Details<img width="1907" height="1010" alt="Screenshot 2026-07-20 120035" src="https://github.com/user-attachments/assets/5dd58c0c-25f7-49d3-80bc-069db1fa7da8" />

* IAM Console Login Page -
 DemoUser<img width="1907" height="1013" alt="Screenshot 2026-07-20 114220" src="https://github.com/user-attachments/assets/5ef72347-34ae-4ecb-b7f9-eaa388dffe53" />
*DemoUser1<img width="1907" height="1008" alt="Screenshot 2026-07-20 114733" src="https://github.com/user-attachments/assets/ca7cefec-1bc0-4da4-b8c7-33c3733173c5" />


---

# Conclusion

Successfully explored AWS Identity and Access Management (IAM), created IAM Users, Groups, Roles, and Policies, and learned how to securely control access to AWS resources using the principle of least privilege.
