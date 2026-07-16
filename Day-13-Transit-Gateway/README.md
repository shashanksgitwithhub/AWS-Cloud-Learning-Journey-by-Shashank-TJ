<p align="center">
  <img src="https://img.shields.io/badge/AWS-Transit Gateway-blueviolet" alt="AWS Badge">
</p>

# ☁ Day 13 - Amazon Transit Gateway

## Objective

To understand Amazon Transit Gateway and learn how it simplifies communication between multiple Virtual Private Clouds (VPCs) and on-premises networks using a centralized hub.

---

# What is Amazon Transit Gateway?

Amazon Transit Gateway (TGW) is a fully managed AWS networking service that acts as a central hub for connecting multiple VPCs, VPNs, and Direct Connect gateways.

Instead of creating multiple VPC Peering connections, Transit Gateway provides a single centralized network through which all attached networks can communicate.

---

# Why Do We Need Transit Gateway?

When the number of VPCs increases, VPC Peering becomes difficult to manage.

For example:

* 2 VPCs → 1 Peering Connection
* 3 VPCs → 3 Peering Connections
* 5 VPCs → 10 Peering Connections

Managing these connections becomes complex.

Transit Gateway solves this by acting as a central router.

---

# Features of Transit Gateway

* Centralized network management
* Connects multiple VPCs
* Supports VPN and AWS Direct Connect
* Scalable architecture
* Simplified routing
* High availability

---

# Transit Gateway Architecture

<img width="842" height="562" alt="Transit_Gateway drawio" src="https://github.com/user-attachments/assets/efc3c16b-68d1-47d9-af02-e58b505206af" />

---

# Transit Gateway Attachments

A Transit Gateway Attachment is the connection between the Transit Gateway and another network resource.

Examples:

* VPC Attachment
* VPN Attachment
* Direct Connect Attachment

Without an attachment, communication is not possible.

---

# Practical Performed

## Step 2: Create three VPC's

```
VPC-A
VPC-B
VPC-C
```

## Step 3: Create each subnets in each VPC's

```
VPC-A-Subnet
VPC-B-Subnet
VPC-C-Subnet
```

## Step 4: Launch EC2 instances in different VPC's

```
Server-VPC-A
Server-VPC-B
Server-VPC-C
```

## Step 5: Create a Transit Gateway

Navigate to:

```text
VPC → Transit Gateways
```

Click:

```text
Create Transit Gateway
```

Configuration:

* Name: My-Transit-Gateway
* Amazon Side ASN: Default
* Auto Accept Shared Attachments: Disabled (Default)

Create the Transit Gateway.

---

## Step 6: Create Transit Gateway Attachments

Navigate to:

```text
VPC → Transit Gateway Attachments
```

Click:

```text
Create Transit Gateway Attachment
```

Select:

* Transit Gateway
* VPC-A

Choose the required subnet.

Repeat the same process for:

* VPC-B
* VPC-C

---

## Step 7: Update Route Tables

For each VPC Route Table:

Add routes pointing to the Transit Gateway.

Example:

| Destination | Target          |
| ----------- | --------------- |
| 10.0.0.0/16 | Transit Gateway |
| 11.0.0.0/16 | Transit Gateway |
| 12.0.0.0/16 | Transit Gateway |

---

## Step 8: Verify Connectivity

Test communication using private IP addresses.

Example:

```bash
ping <Private-IP>
```

If successful, the Transit Gateway is routing traffic correctly.

---

# Practical Outcome

✅ Created a Transit Gateway.

✅ Created Transit Gateway Attachments.

✅ Connected multiple VPCs.

✅ Updated Route Tables.

✅ Verified communication between VPCs.

---

# Advantages of Transit Gateway

* Centralized routing
* Easy management
* Highly scalable
* Supports hybrid cloud connectivity
* Reduces network complexity

---

# VPC Peering vs Transit Gateway

| VPC Peering              | Transit Gateway         |
| ------------------------ | ----------------------- |
| Connects two VPCs        | Connects many VPCs      |
| Not transitive           | Centralized routing     |
| Complex with many VPCs   | Easy to manage          |
| Many peering connections | Single hub architecture |

---

# Key Learnings

* Learned the purpose of Amazon Transit Gateway.
* Understood why Transit Gateway is preferred over multiple VPC Peerings.
* Created Transit Gateway Attachments.
* Updated Route Tables.
* Established centralized communication between multiple VPCs.

---

# Interview Questions

### What is Amazon Transit Gateway?

Amazon Transit Gateway is a centralized networking service that connects multiple VPCs, VPNs, and Direct Connect gateways.

---

### Why is Transit Gateway used instead of VPC Peering?

Transit Gateway simplifies network management by replacing multiple peering connections with a centralized hub.

---

### What is a Transit Gateway Attachment?

A Transit Gateway Attachment connects a VPC, VPN, or Direct Connect gateway to the Transit Gateway.

---

### Is Transit Gateway transitive?

Yes.

If:

VPC-A → Transit Gateway ← VPC-B

VPC-A can communicate with VPC-B through the Transit Gateway.

---

### Can Transit Gateway connect on-premises networks?

Yes.

It supports:

* AWS Site-to-Site VPN
* AWS Direct Connect

---

# Screenshots

* Transit Gateway Dashboard
* Transit Gateway Creation
* Transit Gateway Attachment
* Route Table Configuration
* Attached VPCs
* Successful Connectivity Test

---

# Conclusion

Successfully created an Amazon Transit Gateway, attached multiple VPCs, configured Route Tables, and established centralized communication between networks. Transit Gateway significantly simplifies AWS networking by reducing the complexity associated with multiple VPC Peering connections.
