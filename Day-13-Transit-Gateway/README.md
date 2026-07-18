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

Performed these commands:

```bash
curl 10.0.1.82
ping www.google.com
```
Repeat these in other two servers terminal 

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

* Create three VPCs<img width="1907" height="1009" alt="Screenshot 2026-07-16 103911" src="https://github.com/user-attachments/assets/f6b11a8c-3016-45f2-9ff5-73efc2d54f3c" />
  <img width="1907" height="1011" alt="Screenshot 2026-07-16 104134" src="https://github.com/user-attachments/assets/7728a7a0-a4b3-41cd-9682-661919f68f68" />
  <img width="1907" height="1011" alt="Screenshot 2026-07-16 104457" src="https://github.com/user-attachments/assets/a0284b88-93bd-4c55-ac6c-a9d4baae04a9" />
* Transit Gateway Creation<img width="1907" height="1011" alt="Screenshot 2026-07-16 105312" src="https://github.com/user-attachments/assets/98b27596-7bb8-4645-b9f6-4c5ccb5a5f9a" />
  <img width="1907" height="1010" alt="Screenshot 2026-07-16 105321" src="https://github.com/user-attachments/assets/de2b0b12-21bc-45e3-a1c1-a4f5c8e17592" />
  <img width="1907" height="1011" alt="Screenshot 2026-07-16 105558" src="https://github.com/user-attachments/assets/6ad7be54-1a58-425d-916d-a12ae2e54fd8" />
* Transit Gateway Attachment<img width="1904" height="1009" alt="Screenshot 2026-07-16 105750" src="https://github.com/user-attachments/assets/b12b0812-1d24-49ab-8f52-7d4d787b15b7" />
  <img width="1907" height="1011" alt="Screenshot 2026-07-16 105757" src="https://github.com/user-attachments/assets/d661399b-45f1-4a32-855c-3c2c47eec7ff" />
  <img width="1907" height="1010" alt="Screenshot 2026-07-16 105836" src="https://github.com/user-attachments/assets/94b24663-afb8-4458-a612-c98df96f7a6a" />
  <img width="1907" height="1010" alt="Screenshot 2026-07-16 105846" src="https://github.com/user-attachments/assets/d1af3303-d41e-46fb-8e3a-015b989e7599" />
  <img width="1907" height="1010" alt="Screenshot 2026-07-16 105906" src="https://github.com/user-attachments/assets/0ec3f4a5-f4c0-45aa-a2c6-df491dd7c0a9" />
  <img width="1907" height="1013" alt="Screenshot 2026-07-16 105918" src="https://github.com/user-attachments/assets/e0b3ad9c-2c18-458f-86bd-6c9c65f8403b" />
  <img width="1907" height="1011" alt="Screenshot 2026-07-16 110043" src="https://github.com/user-attachments/assets/fccac2b8-6ced-4d0e-9fdc-239059ccadd2" />
* Create three EC2 instances<img width="1907" height="1014" alt="Screenshot 2026-07-16 104740" src="https://github.com/user-attachments/assets/cd475675-a3b3-46ba-aaab-ecf5fc3c16db" />
  <img width="1907" height="1015" alt="Screenshot 2026-07-16 104856" src="https://github.com/user-attachments/assets/44189fa1-e6c0-44ae-a6d7-f88bb67f275c" />
  <img width="1907" height="1011" alt="Screenshot 2026-07-16 105035" src="https://github.com/user-attachments/assets/80be2157-c08a-4fc4-b9a0-cb96738b3e6c" />
* Route Table Configuration<img width="1907" height="1010" alt="Screenshot 2026-07-16 110200" src="https://github.com/user-attachments/assets/2b98b9f4-31b4-40cd-9ef4-59e0e91f864b" />
  <img width="1907" height="1011" alt="Screenshot 2026-07-16 110212" src="https://github.com/user-attachments/assets/f29b3ea4-59da-4b74-81b8-1a9ff2ddb49d" />
  <img width="1907" height="1008" alt="Screenshot 2026-07-16 110246" src="https://github.com/user-attachments/assets/0499ff41-75a3-421f-b9b6-57b2680e5634" />
  <img width="1907" height="1011" alt="Screenshot 2026-07-16 110257" src="https://github.com/user-attachments/assets/a64638e6-4975-438a-83a5-6ff652acd3b0" />
  <img width="1907" height="1011" alt="Screenshot 2026-07-16 110408" src="https://github.com/user-attachments/assets/e6e4378a-69f7-4939-902c-74dfd6f3ce55" />
  <img width="1907" height="1013" alt="Screenshot 2026-07-16 110416" src="https://github.com/user-attachments/assets/7a93a5e6-3066-4604-91c2-8e824ee64ffb" />
* Open MoaXterm<img width="1907" height="1012" alt="Screenshot 2026-07-16 110429" src="https://github.com/user-attachments/assets/ac579f0b-841e-49a9-aa47-dddf8780a9dd" />
* Successful Connectivity Test<img width="1907" height="1012" alt="Screenshot 2026-07-18 120814" src="https://github.com/user-attachments/assets/397d9fd3-e874-452d-ab31-1fecc534c171" />

---

# Conclusion

Successfully created an Amazon Transit Gateway, attached multiple VPCs, configured Route Tables, and established centralized communication between networks. Transit Gateway significantly simplifies AWS networking by reducing the complexity associated with multiple VPC Peering connections.
