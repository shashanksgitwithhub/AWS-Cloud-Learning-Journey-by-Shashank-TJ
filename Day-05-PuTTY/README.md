<p align="center">
  <img src="https://img.shields.io/badge/AWS-EC2-orange" alt="AWS Badge">
</p>

# ☁ Day 05 - Connecting to EC2 using PuTTY

## Objective

To learn how to connect to an Amazon EC2 instance using PuTTY.

---

# What is PuTTY?

PuTTY is a free SSH client used to connect to Linux servers from Windows.

---

# Prerequisites

* Running EC2 Instance
* Public IP Address
* Port 22 Open
* .pem Key Pair
* PuTTYgen

---

# Launch the instance

## Step 1

Name:

```
Server_PuTTY
```

## Step 2

Choose AMI:

```
Ubuntu
```
## Step 3

Select virtual server:

```
t3.micro
```

# While selecting the key pain (login)

Since PuTTY uses .ppk files:

## Step 1

Create:

```
Create a new key pair for putty
```

## Step 2

Enter:

```text id="jv6cxg"
Give the name as putty_key
```

Select:

```text id="3d0br9"
Key pair type - RSA
Private key file format - .ppk
```

## Step 3

Create:

```text id="yizc30"
Create key pair
```

## Step 4

Launch:

```
Launch the instance
```

---

# Connecting Using PuTTY

## Step 1

Open PuTTY.

## Step 2

Enter:

```text id="2b7axm"
Host Name (or IP address):
18.61.159.236
```
## Step 3

Select:

```
Connection type - SSH
```

## Step 4

Navigate:

```text id="qqlztm"
Connection → SSH → Auth → Credentials
```

## Step 4

Browse and select the private key file for authentication:

```text id="m7f4x8"
putty_key.ppk
```

## Step 5

Click:

```text id="c0v5fk"
Open → Accept
```

## Step 6

Login:

```
Login as ubuntu, if using AMI as Ubuntu
```

## Step 7

Running:

```
The Server starts running
```

---

# Commands Executed

```bash id="5mejlwm"
hostname
pwd
ls
whoami
```

---

# Key Learnings

✅ Converted .pem to .ppk.

✅ Connected to EC2 using PuTTY.

✅ Understood SSH authentication using key files.

---

# Interview Questions

### What is PuTTY?

A terminal emulator and SSH client for Windows.

### Why is PuTTYgen required?

To convert .pem files into .ppk format.

### Which protocol is used?

SSH.

### Which port is used?

Port 22.

---

# Screenshots

* EC2 Dashboard<img width="1918" height="1017" alt="Screenshot 2026-07-03 212747" src="https://github.com/user-attachments/assets/eb4505d2-f97f-49ce-81d4-263088950487" />

* Launch an instance<img width="1918" height="1017" alt="Screenshot 2026-07-03 212915" src="https://github.com/user-attachments/assets/d18196d3-fad1-4fb7-978e-3b6c6e7a9556" />

* Create key pair<img width="1907" height="1007" alt="Screenshot 2026-07-03 214005" src="https://github.com/user-attachments/assets/19316814-4b08-4644-b5e3-aca5b1400322" />

* Launching instance<img width="1907" height="1008" alt="Screenshot 2026-07-03 214033" src="https://github.com/user-attachments/assets/d2bbebe9-74ff-4ffc-930d-f570a2506522" />

* Server_PuTTY running<img width="1907" height="1010" alt="Screenshot 2026-07-03 214130" src="https://github.com/user-attachments/assets/4d607a8b-83d1-4c8b-acca-027293a7b7bc" />

* Open PuTTY application<img width="1907" height="1008" alt="Screenshot 2026-07-03 214152" src="https://github.com/user-attachments/assets/0d82d50f-e207-4d8a-9d67-5931e0c97487" />

* Enter Hostname (or IP address)<img width="1907" height="1008" alt="Screenshot 2026-07-03 214301" src="https://github.com/user-attachments/assets/3799b653-d4e0-4624-b9c9-f727e7d592f2" />

* Browse private key<img width="1907" height="1011" alt="Screenshot 2026-07-03 214353" src="https://github.com/user-attachments/assets/f4cd8608-8260-476c-aeac-faf38b1eabee" />

* Click Accept<img width="1907" height="1011" alt="Screenshot 2026-07-03 214420" src="https://github.com/user-attachments/assets/a330835e-0e02-4ebb-a656-473c69e9f47c" />

* Login as ubuntu<img width="1907" height="178" alt="Screenshot 2026-07-03 214507" src="https://github.com/user-attachments/assets/16adcede-ee97-4018-bdfb-d0e50bda3e9d" />

* Server running with Terminal Commands<img width="1907" height="1009" alt="Screenshot 2026-07-03 214600" src="https://github.com/user-attachments/assets/c17f76b3-0475-4573-8e6f-1292f740e29b" />
