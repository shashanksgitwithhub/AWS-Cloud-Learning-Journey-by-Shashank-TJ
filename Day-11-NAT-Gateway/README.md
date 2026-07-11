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

```text
                     Internet
                         │
                  Internet Gateway
                         │
                Public Subnet
                         │
                  NAT Gateway
                         │
        ┌────────────────┴────────────────┐
        │                                 │
  Private Subnet                    EC2 Instance
                                   (No Public IP)
```

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

## Step 1: Allocate an Elastic IP

Navigate to:

VPC → NAT Gateways

Click:

Create NAT Gateway

Allocate a new Elastic IP.

---

## Step 2: Create NAT Gateway

Configuration:

* Name: My-NAT-Gateway
* Subnet: Public Subnet
* Connectivity Type: Public
* Elastic IP: Allocated Elastic IP

Click:

Create NAT Gateway

Wait until the status becomes **Available**.

---

## Step 3: Configure the Private Route Table

Navigate to:

VPC → Route Tables

Select the Route Table associated with the Private Subnet.

Edit Routes.

Add:

| Destination | Target      |
| ----------- | ----------- |
| 0.0.0.0/0   | NAT Gateway |

Save the changes.

---

## Step 4: Verify Connectivity

Launch an EC2 instance in the Private Subnet.

Connect through a Bastion Host or another secure method if required.

Run:

```bash
sudo apt update
```

or

```bash
ping google.com
```

The instance should be able to access the internet for outbound requests while remaining inaccessible from the public internet.

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

* VPC Architecture
* NAT Gateway Creation
* Elastic IP Allocation
* Route Table Configuration
* NAT Gateway Status (Available)
* Private Route Table showing 0.0.0.0/0 → NAT Gateway
* EC2 Instance in Private Subnet

---

# Conclusion

Successfully created an Amazon NAT Gateway, configured routing for a private subnet, and enabled secure outbound internet connectivity for EC2 instances without exposing them to direct inbound internet access.
