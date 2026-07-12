<p align="center">
  <img src="https://img.shields.io/badge/AWS-NAT Gateway-blueviolet" alt="AWS Badge">
</p>

# ☁ Day 11 - Amazon NAT Gateway

## Objective

To understand the purpose of an Amazon NAT Gateway and learn how it enables instances in a private subnet to access the internet securely without exposing them to inbound internet traffic.

---

# What is a NAT Gateway?

A NAT (Network Address Translation) Gateway is a managed AWS networking service that allows EC2 instances in a **private subnet** to access the internet for outbound communication while preventing inbound connections from the internet.

Examples of outbound access:

* Installing software updates
* Downloading packages
* Accessing AWS services
* Connecting to external APIs

---

# Why Do We Need a NAT Gateway?

EC2 instances in a private subnet do not have a Public IP Address and cannot communicate directly with the internet.

A NAT Gateway solves this problem by allowing **outbound internet access** while keeping the instances private and secure.

---

# NAT Gateway Architecture

<img width="1042" height="732" alt="NAT-Gateway drawio (1)" src="https://github.com/user-attachments/assets/7a80b883-96b5-4f85-af48-501dc1dc5e01" />

---

# Prerequisites

Before creating a NAT Gateway:

* Existing VPC
* Public Subnet
* Private Subnet
* Internet Gateway attached to the VPC
* Elastic IP Address

---

# Practical Performed

## Step 1: Create:

```
1. VPC
2. Internet Gateway
3. Subnets --> Public_subnet, Private_subnet
4. Route table --> RT-Public - assosiate with Public_subnet - Edit routes - Give internet, RT-Private - assosiate with Private_subnet
5. EC2 instance --> Public_Server, Private_Server
```

---

## Step 2: Connect to Public_Server:

Check the interet:

```
ping www.google.com
```

## Step 3: Commands to connect to Private_server through Public_Server terminal:

Run these commands:

```
ls
vi vpckey.pem
```

```
I - insert --> copy the vpckey.pem data and paste.
esc
:wq --> enter
```

```
ls -l --> list files and directories in a long listing format.
ex: -rw-r--r--, 1 ec2-user ec2-user 1679 Jul 12 06:13 vpckey.pem
```

Change to only read:
```
chmod 400 "vpckey.pem"
ex: -r------, 1 ec2-user ec2-user 1679 Jul 12 06:13 vpckey.pem
```

## Step 4: Connect to Private_Server

Private_Server - SSH client
```
ssh -i "vpckey.pem" ec2-user@10.0.3.83
```

```
hostname
ex: ip-10-0-3-83.ap-south-2.compute.internal
```

## Step 5: Access internet to the Private_Server:

Create NAT-Gateway
Configuration:

* Name: NAT-Demo
* Subnet: Public Subnet
* Connectivity Type: Public
* Elastic IP: Allocated Elastic IP

Click:

Create NAT Gateway

Wait until the status becomes **Available**.

---

## Step 6: Configure the Private Route Table

Navigate to:

VPC → Route Tables

Select the RT-Private

Edit Routes.

Add:

| Destination | Target      |
| ----------- | ----------- |
| 0.0.0.0/0   | NAT Gateway |

Save the changes.

---

## Step 7: Verify Connectivity

Go back to the terminal

Run:

```bash
ping www.google.com
```

* The instance should be able to access the internet for outbound requests while remaining inaccessible from the public internet.

* The Private_Server ready to access

---

# Advantages of NAT Gateway

* Secure outbound internet access
* Managed by AWS
* Highly available within an Availability Zone
* No server maintenance required
* Scales automatically

---

# Key Learnings

* Understood the purpose of a NAT Gateway.
* Learned why private subnets require NAT for internet access.
* Created and configured a NAT Gateway.
* Associated the NAT Gateway with the Private Route Table.
* Enabled outbound internet connectivity for private EC2 instances.

---

# Interview Questions

### What is a NAT Gateway?

A NAT Gateway allows resources in a private subnet to access the internet without exposing them to inbound internet traffic.

---

### Why is a NAT Gateway placed in a Public Subnet?

Because it requires internet access through an Internet Gateway to forward outbound traffic.

---

### Can an EC2 instance in a private subnet receive inbound traffic from the internet through a NAT Gateway?

No. A NAT Gateway only allows outbound connections initiated from the private subnet.

---

### What is the difference between an Internet Gateway and a NAT Gateway?

| Internet Gateway                               | NAT Gateway                             |
| ---------------------------------------------- | --------------------------------------- |
| Used by Public Subnets                         | Used by Private Subnets                 |
| Supports inbound and outbound internet traffic | Supports outbound internet traffic only |
| Requires Public IP                             | Uses an Elastic IP                      |

---

# Screenshots to Add

* VPC<img width="1907" height="1009" alt="Screenshot 2026-07-12 113810" src="https://github.com/user-attachments/assets/97e6ad12-42fe-43e9-a012-ce73175b14f4" />
* Internet Gateway<img width="1907" height="1006" alt="Screenshot 2026-07-12 113822" src="https://github.com/user-attachments/assets/6d11b1c4-a1ba-408b-a71b-673b49232243" />
* Subnets<img width="1907" height="1011" alt="Screenshot 2026-07-12 113832" src="https://github.com/user-attachments/assets/f7e6910c-a0bb-4cf0-8c0a-33b09139dd26" />
  <img width="1907" height="1007" alt="Screenshot 2026-07-12 113842" src="https://github.com/user-attachments/assets/6505b997-daef-4fb5-b1d5-9bea37cc3dcc" />
* Route tables<img width="1907" height="1007" alt="Screenshot 2026-07-12 113927" src="https://github.com/user-attachments/assets/305440ea-b0ef-47fc-9c79-0e7ca6e65cc2" />
  <img width="1907" height="1011" alt="Screenshot 2026-07-12 113934" src="https://github.com/user-attachments/assets/4b46cf2c-688c-4ca4-a4ac-6136cc8c23a8" />
  <img width="1907" height="1008" alt="Screenshot 2026-07-12 113946" src="https://github.com/user-attachments/assets/6124b881-8c44-4fa3-a4d8-b666a50c85bd" />
  <img width="1907" height="1007" alt="Screenshot 2026-07-12 113954" src="https://github.com/user-attachments/assets/c0226b78-7443-40e1-8a6a-28dfcc139af7" />
* EC2 instance<img width="1907" height="1009" alt="Screenshot 2026-07-12 114017" src="https://github.com/user-attachments/assets/bc36638b-eb6b-4208-8bcb-60b4af034014" />
  <img width="1907" height="1011" alt="Screenshot 2026-07-12 114029" src="https://github.com/user-attachments/assets/cfd56497-8b47-4693-a80f-9ea7db85011e" />
* Public_Server Terminal<img width="1907" height="1010" alt="Screenshot 2026-07-12 114205" src="https://github.com/user-attachments/assets/efa3d29b-95c6-4c3f-87fc-4d5ead2721ba" />
  <img width="1907" height="1009" alt="Screenshot 2026-07-12 114619" src="https://github.com/user-attachments/assets/503e3600-6806-45f1-95be-d852763ef866" />
  <img width="1907" height="1009" alt="Screenshot 2026-07-12 114656" src="https://github.com/user-attachments/assets/66b70308-5e7e-42c6-9cff-40cb4f4b8825" />
  <img width="1906" height="1008" alt="Screenshot 2026-07-12 115003" src="https://github.com/user-attachments/assets/758154a0-daa8-4917-90ce-22f0e13ccdae" />
  <img width="1907" height="1009" alt="Screenshot 2026-07-12 115053" src="https://github.com/user-attachments/assets/a40ba922-5ee1-440d-a5b3-dcf7b362eeb7" />
  <img width="1907" height="1012" alt="Screenshot 2026-07-12 115500" src="https://github.com/user-attachments/assets/6474c294-b938-476e-9633-3f7a0f1fa480" />
  <img width="1907" height="1009" alt="Screenshot 2026-07-12 115721" src="https://github.com/user-attachments/assets/b7c9d27b-e9b1-48f4-8997-d793cf0fe6d8" />
* NAT Gateway Creation and Elastic IP Allocation
  <img width="1907" height="1009" alt="Screenshot 2026-07-12 120258" src="https://github.com/user-attachments/assets/805c2781-8b45-47bc-a2a7-3a16150c2c7d" />
  <img width="1907" height="1010" alt="Screenshot 2026-07-12 120527" src="https://github.com/user-attachments/assets/a303177c-2ff6-4581-90e6-e725c3e815d7" />
  <img width="1907" height="1010" alt="Screenshot 2026-07-12 120527" src="https://github.com/user-attachments/assets/c6e4521c-d146-449e-a929-9b51d0816261" />
  <img width="1907" height="1006" alt="Screenshot 2026-07-12 120539" src="https://github.com/user-attachments/assets/7eea0134-f0d3-4dd7-83e6-6cfebbab5ba1" />
  <img width="1907" height="1010" alt="Screenshot 2026-07-12 120950" src="https://github.com/user-attachments/assets/2b014819-c598-457e-98b1-6f11d020ca03" />
* Route Table Configuration<img width="1907" height="1010" alt="Screenshot 2026-07-12 121125" src="https://github.com/user-attachments/assets/44d1492e-8c31-46eb-98d6-24070606a3c7" />
  <img width="1907" height="1009" alt="Screenshot 2026-07-12 121144" src="https://github.com/user-attachments/assets/5eab09e2-7203-4c35-a777-132669fadf7a" />
  <img width="1907" height="1009" alt="Screenshot 2026-07-12 121157" src="https://github.com/user-attachments/assets/d407126e-5f42-454f-b0b7-07bd877050ed" />
* EC2 Instance in Private Subnet<img width="1907" height="1010" alt="Screenshot 2026-07-12 121229" src="https://github.com/user-attachments/assets/27ddc3ee-8a62-4838-9a79-54cc9bf9c252" />

---

# Conclusion

Successfully created an Amazon NAT Gateway, configured routing for a private subnet, and enabled secure outbound internet connectivity for EC2 instances without exposing them to direct inbound internet access.
