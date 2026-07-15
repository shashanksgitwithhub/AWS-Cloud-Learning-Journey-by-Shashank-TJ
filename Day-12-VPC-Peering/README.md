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

<img width="721" height="361" alt="VPC_Peering drawio" src="https://github.com/user-attachments/assets/b94a2678-f8ae-4a71-935f-469e84c27245" />

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

VPC-1

```text
CIDR: 10.0.0.0/16
```

VPC-2

```text
CIDR: 11.0.0.0/16
```

---

## Step 2: Create subnet for each VPC

VPC-1

```
VPC-1-Subnet-1
```

VPC-2

```
VPC-2-Subnet-1
```

---

## Step 3: Create route tables for each VPC

VPC-1

```
RT-VPC-1
Save subnet association --> VPC-1-Subnet-1
Edit routes --> give internet gateway
```

VPC-2

```
RT-VPC-2
Save subnet association --> VPC-2-Subnet-1
Edit routes --> give internet gateway
```

---

## Step 4: Create VPC Peering Connection

Navigate to:

```text
VPC → Peering Connections
```

Click:

```text
Create Peering Connection
```

Configuration:
* Name - VPC-peering-demo
* Requester VPC → VPC-1
* Accepter VPC → VPC-2

---

## Step 5: Accept the Peering Request

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

## Step 6: Launch EC2 instance in each subnet

VPC-1-Subnet-1
```
VPC-1-Server
```

VPC-2-Subnet-1
```
VPC-2-Server
```

---

## Step 7: Update Route Tables

### Route Table of VPC-1

Add:

| Destination | Target             |
| ----------- | ------------------ |
| 11.0.0.0/16 | Peering Connection |

---

### Route Table of VPC-2

Add:

| Destination | Target             |
| ----------- | ------------------ |
| 10.0.0.0/16 | Peering Connection |

---

## Step 8: Test Connectivity in MobaXterm

Open the MobaXterm:

Navigate:
```
# VPC-1-Server
Sessions --> SSH
Paste: Remote host -- Public IPv4 address of VPC-1-Server
Username: ubuntu
Advance SSH settings
✅ Use private key --> browse -- private key -- UBkey
OK
```

```
# VPC-2-Server
Sessions --> SSH
Paste: Remote host -- Public IPv4 address of VPC-2-Server
Username: ubuntu
Advance SSH settings
✅ Use private key --> browse -- private key -- UBkey
OK
```

Split two terminal modes:

```
We should see two terminal screens
```

Perform these commands:

Example:
```
curl 10.0.1.136
ping www.google.com
```
Perform these commands in each of the terminal in order to check the VPC peering connections.


Successful replies confirm that the VPC Peering connection is working correctly.

---

# Practical Outcome

✅ Created two VPCs.

✅ Established a VPC Peering connection.

✅ Updated Route Tables.

✅ Verified communication using private IP addresses.

---

# Advantages of VPC Peering

* Private communication
* High performance
* Low latency
* Secure AWS backbone network

---

# Key Learnings

* Learned how VPC Peering connects two VPCs.
* Understood the importance of Route Tables.
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

VPC-1 ↔ VPC-2

VPC-2 ↔ VPC-3

Then:

VPC-1 ❌ cannot communicate with VPC-3 through VPC-2.

---

# Screenshots

* VPC-1 Details<img width="1917" height="1015" alt="Screenshot 2026-07-15 115242" src="https://github.com/user-attachments/assets/c1b94e53-086e-4c0d-930c-81fb9978832a" />
* VPC-2 Details<img width="1917" height="1016" alt="Screenshot 2026-07-15 115252" src="https://github.com/user-attachments/assets/26d9dbcd-e691-4417-a179-9640bcd86b77" />
* Subnets<img width="1917" height="1018" alt="Screenshot 2026-07-15 115620" src="https://github.com/user-attachments/assets/24766400-56ff-40e3-af2b-d388c77a5f1d" />
* Route tables<img width="1917" height="1015" alt="Screenshot 2026-07-15 115919" src="https://github.com/user-attachments/assets/fa2f7f9a-bbf2-48e3-8f67-21e200bb0fc8" />
  <img width="1917" height="1017" alt="Screenshot 2026-07-15 115943" src="https://github.com/user-attachments/assets/d2a0e557-8d52-4a5c-aa05-5e99413b6d2f" />
  <img width="1917" height="1020" alt="Screenshot 2026-07-15 120004" src="https://github.com/user-attachments/assets/1284d9c6-6f09-4b98-9845-68fc41b33f5f" />
  <img width="1917" height="1017" alt="Screenshot 2026-07-15 120019" src="https://github.com/user-attachments/assets/3e78b34b-f83e-4f23-abe7-f288b5db9948" />
  <img width="1917" height="1015" alt="Screenshot 2026-07-15 120034" src="https://github.com/user-attachments/assets/ba344ff0-e773-4358-93aa-493077ea7619" />
* Peering Connection Creation<img width="1917" height="1018" alt="Screenshot 2026-07-15 120205" src="https://github.com/user-attachments/assets/cbcdab5e-2926-40bb-af34-248aedfd27c2" />
  <img width="1917" height="1016" alt="Screenshot 2026-07-15 120215" src="https://github.com/user-attachments/assets/8c77a528-ca64-432d-9ac9-52b431219a95" />
* Peering Connection Status (Active)<img width="1917" height="1017" alt="Screenshot 2026-07-15 120229" src="https://github.com/user-attachments/assets/5cf4cddb-9442-4131-8d15-c73155437c1e" />
  <img width="1917" height="1016" alt="Screenshot 2026-07-15 120240" src="https://github.com/user-attachments/assets/37332902-9888-48d6-930e-353d48683dcf" />
* Launch EC2 instances<img width="1917" height="1015" alt="Screenshot 2026-07-15 120505" src="https://github.com/user-attachments/assets/78f1bfab-8324-4d15-aba0-3c843a33ac72" />
  <img width="1917" height="1017" alt="Screenshot 2026-07-15 120612" src="https://github.com/user-attachments/assets/f82b065c-e09e-4144-9dbc-9af479a4b304" />
* Update routes -- peering connections -- RT-VPC-1 and RT-VPC-2
  <img width="1917" height="1017" alt="Screenshot 2026-07-15 120748" src="https://github.com/user-attachments/assets/2f48bcd3-2f03-4359-b4ce-8b8e52a044b2" />
  <img width="1917" height="1017" alt="Screenshot 2026-07-15 120804" src="https://github.com/user-attachments/assets/2ab5ae48-ff32-456a-9835-77fbdb2ad48a" />
  <img width="1917" height="1018" alt="Screenshot 2026-07-15 120827" src="https://github.com/user-attachments/assets/ea0b6659-a2bb-4dda-ba2e-332a4e81a100" />
  <img width="1917" height="1016" alt="Screenshot 2026-07-15 120837" src="https://github.com/user-attachments/assets/daafd90c-0c76-43b2-9343-ec1ca5b9866f" />
* MobaXterm<img width="1917" height="1018" alt="Screenshot 2026-07-15 120855" src="https://github.com/user-attachments/assets/9d6038c8-93aa-40ff-87ff-30fd842f5edb" />
* Successful Ping Between EC2 Instances<img width="1917" height="1017" alt="Screenshot 2026-07-15 121259" src="https://github.com/user-attachments/assets/125f62e2-0c9f-4d7a-b34b-fa53a86ea28b" />

---

# Conclusion

Successfully created an Amazon VPC Peering connection between two VPCs, updated Route Tables and Security Groups, and established secure private communication between AWS resources without using the public internet.
