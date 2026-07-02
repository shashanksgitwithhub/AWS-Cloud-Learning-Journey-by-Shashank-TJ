<p align="center">
  <img src="https://img.shields.io/badge/AWS-EC2-orange" alt="AWS Badge">
</p>

# ☁ Day 04 - Connecting to EC2 using MobaXterm

## Objective

To learn how to connect to an Amazon EC2 instance using the MobaXterm SSH client.

---

# What is MobaXterm?

MobaXterm is a third-party terminal application that provides SSH, SFTP, and remote session management for Windows users.

---

# Prerequisites

* Running EC2 Instance
* Public IP Address
* SSH Port 22 Open
* Downloaded .pem Key Pair

---

# Steps Performed

## Step 1

Launch:

```
Create the EC2 instance 
```

## Step 2

Instance:

```
Keep the instance running 
```

## Step 2

```
Open MobaXterm.
```

## Step 3

Click:

```text id="9z1pj1"
Session
```

## Step 4

Select:

```text id="f0bjlwm"
SSH
```

## Step 5

Enter:

```text id="pcjlwm"
Remote Host: 
16.113.46.253
```

## Step 6

Specify Username:

Ubuntu:

```text id="5xep1r"
ubuntu
```

Amazon Linux:

```text id="mjlwm5"
ec2-user
```

## Step 7

Click on Advance SSH settings

```
Tick mark - Use private key 
```

## Step 8

Browse and select:

```text id="33u2s0"
UBkey.pem
```

## Step 8

Click:

```text id="03h7m7"
OK
```

## Step 9 

Popup message apprears:

```
Connection to 16.113.46.253 (port 22) --> Accept
```

## Step 10

View user interface:

```
The server is accessed by - MobXterm
16.113.46.253 (ubuntu)
```

---

# Commands Executed

```bash id="7sdyf6"
pwd
hostname
ls
whoami
```

---

# Key Learnings

✅ Connected to EC2 using SSH.

✅ Used a .pem key file for authentication.

✅ Learned remote server administration using MobaXterm.

---

# Interview Questions

### What is MobaXterm?

A third-party terminal application used to connect to remote servers using SSH.

### Which protocol is used?

SSH (Secure Shell).

### Which port is used?

Port 22.

---

# Screenshots
* Launch an instance<img width="1907" height="1011" alt="Screenshot 2026-07-02 134554" src="https://github.com/user-attachments/assets/f2af3198-4b41-4a49-8e5a-8a9697eef47f" />

* Instance summary for (EC2-MobXterm)<img width="1907" height="1010" alt="Screenshot 2026-07-02 135727" src="https://github.com/user-attachments/assets/04102e4d-194c-4f85-807b-b888259c5b1f" />

* Open MobXterm<img width="1907" height="1011" alt="Screenshot 2026-07-02 135754" src="https://github.com/user-attachments/assets/287648ef-670a-4efb-982d-d4c9de9e563b" />

* MobXterm Dashboard<img width="1907" height="1010" alt="Screenshot 2026-07-02 135806" src="https://github.com/user-attachments/assets/e0582a0d-821c-4716-a82c-4bf8699cd377" />

* MobaXterm Session Configuration<img width="1907" height="1011" alt="Screenshot 2026-07-02 135816" src="https://github.com/user-attachments/assets/362e761a-5686-4388-855c-9eac1a0094d8" />

* Session settings
    -Basic SSH settings
    -Advance SSH settings<img width="1907" height="1009" alt="Screenshot 2026-07-02 135850" src="https://github.com/user-attachments/assets/09014e76-9ad3-4279-b70a-fa8dd6e05179" />

* Connection to 16.113.46.253 (port 22)<img width="1907" height="1006" alt="Screenshot 2026-07-02 135902" src="https://github.com/user-attachments/assets/466c44eb-7ed3-49aa-92e1-890e4ebcb7ed" />

* Ubuntu server<img width="1907" height="1008" alt="Screenshot 2026-07-02 135917" src="https://github.com/user-attachments/assets/5a41612b-32be-4d4a-82a2-7803bb462c2c" />
   
* Terminal Commands<img width="1907" height="1008" alt="Screenshot 2026-07-02 140035" src="https://github.com/user-attachments/assets/7c526fed-67b5-4869-b2da-992c2c2b05d1" />

