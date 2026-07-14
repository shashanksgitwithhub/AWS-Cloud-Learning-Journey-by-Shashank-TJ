<p align="center">
  <img src="https://img.shields.io/badge/AWS-VPC Peering-blueviolet" alt="AWS Badge">
</p>

# ☁ Day 12 - Amazon VPC Peering

## Objective

To understand Amazon VPC Peering and learn how to establish private communication between two Virtual Private Clouds (VPCs).

---

# What is Amazon VPC Peering?

Amazon VPC Peering is a networking connection between two VPCs that allows resources in both VPCs to communicate privately using their private IPv4 or IPv6 addresses.

Traffic between peered VPCs remains on the AWS network and does not travel over the public internet.

---

# Why Do We Need VPC Peering?

Normally, two VPCs cannot communicate with each other.

VPC Peering allows:

* Private communication between VPCs
* Sharing of resources across VPCs
* Low-latency communication
* Secure network connectivity

---

# Features of VPC Peering

* Private communication using private IP addresses
* No Internet Gateway required
* No VPN required
* Low network latency
* Secure AWS backbone communication

---

# VPC Peering Architecture

```text
                 AWS Cloud

        ┌──────────────────────────┐
        │      VPC-A               │
        │     10.0.0.0/16          │
        │                          │
        │      EC2 Instance        │
        └──────────┬───────────────┘
                   │
           VPC Peering Connection
                   │
        ┌──────────┴───────────────┐
        │      VPC-B               │
        │     20.0.0.0/16          │
        │                          │
        │      EC2 Instance        │
        └──────────────────────────┘
```

---

# Prerequisites

Before creating a VPC Peering connection:

* Two VPCs
* Different CIDR blocks (No overlapping IP ranges)
* Route Tables
* Running EC2 instances (optional for testing)

---

# Practical Performed

## Step 1: Create Two VPCs

Example:

VPC-A

```text
CIDR: 10.0.0.0/16
```

VPC-B

```text
CIDR: 20.0.0.0/16
```

---

## Step 2: Create VPC Peering Connection

Navigate to:

```text
VPC → Peering Connections
```

Click:

```text
Create Peering Connection
```

Configuration:

* Requester VPC → VPC-A
* Accepter VPC → VPC-B

---

## Step 3: Accept the Peering Request

Select the pending request.

Click:

```text
Actions → Accept Request
```

Status changes to:

```text
Active
```

---

## Step 4: Update Route Tables

### Route Table of VPC-A

Add:

| Destination | Target             |
| ----------- | ------------------ |
| 20.0.0.0/16 | Peering Connection |

---

### Route Table of VPC-B

Add:

| Destination | Target             |
| ----------- | ------------------ |
| 10.0.0.0/16 | Peering Connection |

---

## Step 5: Configure Security Groups

Allow the required inbound traffic from the CIDR block of the peer VPC.

Example:

* ICMP (for Ping)
* SSH (Port 22) if required

---

## Step 6: Test Connectivity

Connect to an EC2 instance in VPC-A and ping the private IP address of an EC2 instance in VPC-B.

Example:

```bash
ping <Private-IP-of-EC2-in-VPC-B>
```

Successful replies confirm that the VPC Peering connection is working correctly.

---

# Practical Outcome

✅ Created two VPCs.

✅ Established a VPC Peering connection.

✅ Updated Route Tables.

✅ Configured Security Groups.

✅ Verified communication using private IP addresses.

---

# Advantages of VPC Peering

* Private communication
* High performance
* Low latency
* No Internet Gateway required
* Secure AWS backbone network

---

# Key Learnings

* Learned how VPC Peering connects two VPCs.
* Understood the importance of Route Tables.
* Configured Security Groups for communication.
* Verified private communication between EC2 instances.

---

# Interview Questions

### What is Amazon VPC Peering?

Amazon VPC Peering is a networking connection that enables private communication between two VPCs.

---

### Does VPC Peering require an Internet Gateway?

No. Communication occurs entirely over the AWS private network.

---

### Can peered VPCs have overlapping CIDR blocks?

No. VPCs with overlapping CIDR blocks cannot be peered.

---

### Why must Route Tables be updated after creating a VPC Peering connection?

To direct traffic from one VPC to the other through the peering connection.

---

### Is VPC Peering transitive?

No. VPC Peering is **not transitive**.

Example:

If:

VPC-A ↔ VPC-B

VPC-B ↔ VPC-C

Then:

VPC-A ❌ cannot communicate with VPC-C through VPC-B.

---

# Screenshots to Add

* VPC-A Details
* VPC-B Details
* Peering Connection Creation
* Peering Connection Status (Active)
* Route Table of VPC-A
* Route Table of VPC-B
* Security Group Configuration
* Successful Ping Between EC2 Instances

---

# Conclusion

Successfully created an Amazon VPC Peering connection between two VPCs, updated Route Tables and Security Groups, and established secure private communication between AWS resources without using the public internet.
