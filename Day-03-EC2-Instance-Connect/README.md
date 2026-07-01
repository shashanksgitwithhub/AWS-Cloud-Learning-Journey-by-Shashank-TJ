<p align="center">
  <img src="https://img.shields.io/badge/AWS-EC2-orange" alt="AWS Badge">
</p>

# ☁ Day 03 - Connecting to EC2 using EC2 Instance Connect

## Objective

To learn how to connect to an Amazon EC2 instance directly from the AWS Console using EC2 Instance Connect.

---

# What is EC2 Instance Connect?

EC2 Instance Connect is a browser-based SSH connection service provided by AWS that allows users to securely connect to Linux EC2 instances directly from the AWS Management Console without installing third-party software.

---

# Prerequisites

* Running EC2 Instance
* Public IPv4 Address
* Security Group allowing SSH (Port 22)
* Compatible Linux AMI (Ubuntu/Amazon Linux)

---

# Steps Performed

## Step 1

Open AWS Console.

## Step 2

Navigate to:

```text id="cnz6tr"
EC2 → Instances
```

## Step 3

Create the EC2 instance:

```
Name - EC2_Demo
AMI - linux
Instance type - t3.micro
Key pair (login) - linuxkey
Network settings - Default
```

## Step 4

Launch the EC2 instance:

```
CLick on launch
```

## Step 5

Connect to the Server:

```text id="h0h89h"
Click on Connect 
```

A browser terminal opens and allows direct access to the EC2 instance.

---

# Commands Executed

```bash id="0z0eeh"
pwd
hostname
whoami
ls
mkdir S1 S2 S3 S4
```

---

# Key Learnings

✅ Connected to EC2 without installing additional software.

✅ Understood browser-based SSH access.

✅ Learned the importance of Port 22 in Security Groups.

---

# Interview Questions

### What is EC2 Instance Connect?

A browser-based SSH service that allows users to connect to EC2 instances directly from the AWS Console.

### Which port is required for EC2 Instance Connect?

Port 22 (SSH).

### What is the advantage of EC2 Instance Connect?

No need to install third-party tools or download key files.

---

# Screenshots

* Launch an instance<img width="1906" height="1008" alt="Screenshot 2026-07-01 222526" src="https://github.com/user-attachments/assets/a43161df-e04d-40f6-a8ad-cb906ce72b8d" />

* Running EC2 Instance<img width="1906" height="1013" alt="Screenshot 2026-07-01 223420" src="https://github.com/user-attachments/assets/4cf8ae7d-ac4d-4fe7-865b-aa85a2c7ac93" />

* EC2 Connect Button<img width="1905" height="1010" alt="Screenshot 2026-07-01 223501" src="https://github.com/user-attachments/assets/72a16736-68c5-49d5-8e48-b6cd0bdce8c3" /> <img width="1906" height="1007" alt="Screenshot 2026-07-01 224533" src="https://github.com/user-attachments/assets/a7cdf08c-31e9-489e-8f9a-0f968ef0d520" />

* Browser Terminal<img width="1907" height="1008" alt="Screenshot 2026-07-01 223650" src="https://github.com/user-attachments/assets/8c62f05e-1663-4c43-9110-fcfda7ef98b2" />

