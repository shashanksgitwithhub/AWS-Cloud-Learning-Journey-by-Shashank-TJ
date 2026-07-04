<p align="center">
  <img src="https://img.shields.io/badge/AWS-EC2-orange" alt="AWS Badge">
</p>

# ☁ Day 06 - Connecting to EC2 using Remote Desktop Connection (RDC)

## Objective

To learn how to connect to a Windows EC2 instance using Microsoft's Remote Desktop Connection (RDP) service.

---

# What is Remote Desktop Connection (RDC)?

Remote Desktop Connection (RDC) is a Microsoft feature that allows users to remotely access and control another computer over a network.

In AWS, RDC is commonly used to connect to Windows EC2 instances.

---

# What is RDP?

RDP (Remote Desktop Protocol) is a proprietary protocol developed by Microsoft that enables remote access to Windows servers and desktops.

Default Port:

```text id="55yb5g"
3389
```

---

# Prerequisites

* Running Windows EC2 Instance
* Public IPv4 Address
* Security Group allowing RDP (Port 3389)
* Administrator Password
* Key Pair (.pem file)

---

# Architecture

```text id="dfpkto"
Windows Laptop
       │
       │ RDP (Port 3389)
       │
       ▼
Windows EC2 Instance
```

---

# Steps Performed

## Step 1

Launch a Windows EC2 Instance.

```text id="5t8h2n"
1. Name - Server_Windows

2. AMI - Microsoft Windows Server 2022 Base

3. Instance type - t3.micro

4. Key pair (login) - windowskey.pem

5. Lanuch instance
```

---

## Step 2

Wait for the instance to initialize.

---

## Step 3

Select the EC2 Instance.

Click:

```text id="kk0fup"
Connect
```

---

## Step 4

Choose:

```text id="w5s0fd"
RDP Client
```

---

## Step 5

Download the Remote Desktop File:

```text id="n08l9w"
Download Remote Desktop File
```

---

## Step 6

Get Administrator Password.

Click:

```text id="lcms73"
Get Password
```

Upload:

```text id="w7hz5v"
your-key.pem
```

Click:

```text id="ptd9m8"
Decrypt Password
```

Copy the Administrator password.

---

## Step 7

Open:

```text id="n5ylca"
Remote Desktop Connection
```

Enter:

```text id="0q4tqu"
Public IPv4 Address
```

Click:

```text id="jwlx0v"
Connect
```

---

## Step 8

Login Credentials

Username:

```text id="d7r5s9"
Administrator
```

Password:

```text id="vjlwmf"
<Decrypted Password>
```

---

# Practical Performed

✅ Launched a Windows EC2 instance.

✅ Downloaded the RDP file.

✅ Retrieved the Administrator password.

✅ Connected to the Windows Server remotely.

---

# Key Learnings

* Windows EC2 instances use RDP instead of SSH.
* Port 3389 must be allowed in the Security Group.
* Administrator password is encrypted and must be decrypted using the Key Pair.
* RDC provides full graphical access to the Windows Server.

---

# Interview Questions

### What is RDP?

Remote Desktop Protocol is used to remotely access Windows servers.

---

### Which port does RDP use?

```text id="0n6t4u"
3389
```

---

### Why do we need a Key Pair for Windows EC2?

The private key is used to decrypt the Administrator password.

---

### Difference between SSH and RDP?

| SSH                    | RDP                 |
| ---------------------- | ------------------- |
| Command Line Interface | Graphical Interface |
| Port 22                | Port 3389           |
| Linux Instances        | Windows Instances   |

---

# Screenshots

* Enter name and choose AMI as windows<img width="1907" height="1007" alt="Screenshot 2026-07-04 165503" src="https://github.com/user-attachments/assets/ee6974a6-0255-4864-93c8-dc1a2c39b0b0" />

* Instance type and key pair (login)<img width="1907" height="1010" alt="Screenshot 2026-07-04 170407" src="https://github.com/user-attachments/assets/3b24cf2c-1a28-460f-89d1-d5511108369f" />

* Launch Windows EC2 Instance<img width="1907" height="1010" alt="Screenshot 2026-07-04 170437" src="https://github.com/user-attachments/assets/69f72941-4e88-48ff-a4e2-4d2a99c27a47" />

* Server_Windows running<img width="1907" height="1006" alt="Screenshot 2026-07-04 170703" src="https://github.com/user-attachments/assets/9f25ae4c-9d8c-4b2f-a0c2-b4f6b143bcfd" />

* Connect --> RDP client --> Get password<img width="1907" height="1006" alt="Screenshot 2026-07-04 171020" src="https://github.com/user-attachments/assets/35250921-d873-4647-b474-bb409e7732a2" />

* Upload the private key file<img width="1907" height="1008" alt="Screenshot 2026-07-04 171126" src="https://github.com/user-attachments/assets/673a586d-a973-478f-87e4-c55515e8f918" />

* Decrypt password<img width="1907" height="1007" alt="Screenshot 2026-07-04 171200" src="https://github.com/user-attachments/assets/e91da545-d41e-4b3c-9df4-53dfbe94ba18" />

* Copy Decrypted password<img width="1907" height="1009" alt="Screenshot 2026-07-04 171228" src="https://github.com/user-attachments/assets/0cea6d9f-ac31-47c9-9e28-355712b8dea3" />

* Search and open Remote Desktop connection<img width="1907" height="1010" alt="Screenshot 2026-07-04 170811" src="https://github.com/user-attachments/assets/72a72c51-d187-4300-8f71-57cece34f2d9" />

* Copy the public IP address and paste<img width="1907" height="1008" alt="Screenshot 2026-07-04 170833" src="https://github.com/user-attachments/assets/6ea4dff4-d69b-4cc2-b8a3-3abbb7205319" />

* Enter your Credentials<img width="1918" height="1018" alt="Screenshot 2026-07-04 171404" src="https://github.com/user-attachments/assets/0539e961-766f-4d1b-8d57-64e7bc650653" />

* Connecting <img width="1907" height="1008" alt="Screenshot 2026-07-04 171417" src="https://github.com/user-attachments/assets/76239cf7-26fd-49d5-bc40-c087461dfc42" />

* Connect anyway<img width="1907" height="1000" alt="Screenshot 2026-07-04 171514" src="https://github.com/user-attachments/assets/331b147a-e14f-426c-898c-3042d0f37dd5" />

* Successful Windows Server Login<img width="3988" height="2241" alt="WhatsApp Image 2026-07-04 at 5 22 57 PM" src="https://github.com/user-attachments/assets/756de6c1-11c6-4d4f-b684-785d3a39579b" />


---

# Conclusion

Successfully connected to a Windows EC2 instance using Remote Desktop Connection (RDC) by configuring RDP access, decrypting the Administrator password, and remotely accessing the Windows Server through Port 3389.
****
