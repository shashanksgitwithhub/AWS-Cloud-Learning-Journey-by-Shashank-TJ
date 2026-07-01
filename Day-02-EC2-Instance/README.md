
<p align="center">
  <img src="https://img.shields.io/badge/AWS-EC2-orange" alt="AWS Badge">
</p>

# ☁ Day 02 - Amazon EC2 (Elastic Compute Cloud)

## Objective

To understand Amazon EC2 and learn how to launch, configure, and connect to an EC2 instance and host a simple web page using Apache Web Server.

---

# What is Amazon EC2?

Amazon Elastic Compute Cloud (EC2) is a web service that provides secure and resizable virtual servers in the cloud.

EC2 allows users to launch virtual machines and run applications without purchasing physical hardware.

---

# Features of Amazon EC2

* Resizable virtual servers
* Pay-as-you-go pricing
* Highly scalable
* Multiple operating systems
* Secure and reliable
* Supports various instance types
* Easy integration with other AWS services

---

# Key Components of EC2

## 1. Amazon Machine Image (AMI)

A pre-configured template containing:

* Operating System
* Application Server
* Software Packages

Examples:

* Ubuntu
* Amazon Linux
* Red Hat Enterprise Linux

---

## 2. Instance Type

Defines:

* CPU
* Memory
* Storage
* Network Capacity

Examples:

* t2.micro
* t3.micro
* m5.large

---

## 3. Key Pair

A security credential used to securely connect to an EC2 instance.

Components:

* Public Key
* Private Key (.pem file)

---

## 4. Security Group

Acts as a virtual firewall that controls:

* Inbound Traffic
* Outbound Traffic

Ports Used:

* SSH → Port 22
* HTTP → Port 80
* HTTPS → Port 443

---

## 5. Public IP Address

Used to access the EC2 instance from the internet.

---

# Practical Performed

## Step 1: Launch EC2 Instance

1. Open AWS Console.
2. Navigate to EC2 Dashboard.
3. Click Launch Instance.
4. Select Ubuntu Server AMI.
5. Choose t2.micro instance type.
6. Create a new Key Pair.
7. Configure Security Group rules.
8. Launch the instance.

---

## Step 2: Install Apache Using User Data

### User Data Script

```bash
#!/bin/bash

sudo apt update -y
sudo apt install apache2 -y

sudo systemctl start apache2
sudo systemctl enable apache2

echo "<html><h1>Server Details</h1><p><strong>Hostname:</strong> $(hostname)</p><p><strong>IP Address:</strong> $(hostname -I | awk '{print $1}')</p></html>" | sudo tee /var/www/html/index.html
```

---

## What Does This Script Do?

| Command                    | Purpose                                         |
| -------------------------- | ----------------------------------------------- |
| `apt update`               | Updates package information                     |
| `apt install apache2`      | Installs Apache Web Server                      |
| `systemctl start apache2`  | Starts Apache service                           |
| `systemctl enable apache2` | Enables Apache during reboot                    |
| `echo ... > index.html`    | Creates a webpage displaying server information |

---

## Output

When the Public IP Address is opened in a browser:

```text
16.112.60.33
```

The webpage displays:

```text
Server Details
Hostname: ip-172-31-4-215
IP Address: 172.31.4.215
```

(The values will vary depending on the EC2 instance.)

---

# Key Learnings

✅ Learned how to launch an EC2 instance.

✅ Understood AMI, Instance Types, Key Pairs, and Security Groups.

✅ Installed Apache Web Server using User Data.

✅ Hosted a simple webpage on an EC2 instance.

✅ Accessed the webpage using the Public IP Address.

---

# Interview Questions

### What is Amazon EC2?

Amazon EC2 is a service that provides virtual servers in the cloud.

---

### What is an AMI?

An Amazon Machine Image (AMI) is a template used to create EC2 instances.

---

### What is a Security Group?

A Security Group is a virtual firewall that controls inbound and outbound traffic.

---

### What is a Key Pair?

A Key Pair is used to securely connect to an EC2 instance.

---

### What is User Data in EC2?

User Data is a script that automatically runs when an EC2 instance launches and is commonly used to install software and configure the server.

---

### Difference between Stop and Terminate?

**Stop**

* Instance can be restarted.
* EBS volume is retained.

**Terminate**

* Instance is permanently deleted.
* Resources are released.

---

# Screenshots

* EC2 Dashboard<img width="1917" height="1020" alt="Screenshot 2026-06-30 221103" src="https://github.com/user-attachments/assets/47a6b839-e4e6-4c54-b5a0-30f11ec30f88" />

* Launch Instance Page - Enter name and choose the [AMI]<img width="1917" height="1018" alt="Screenshot 2026-06-30 221333" src="https://github.com/user-attachments/assets/1eb3e727-199a-47f8-bb1c-c9fc159d60c1" />

* Instance type and Key pair<img width="1918" height="1018" alt="Screenshot 2026-06-30 221442" src="https://github.com/user-attachments/assets/9d9ddb38-f6e6-44ec-b965-62e54d3b8183" />

* Network settings - Security Groups<img width="1917" height="1016" alt="Screenshot 2026-06-30 221457" src="https://github.com/user-attachments/assets/8c5d1645-bc44-4f97-a52d-4d9abdb39b16" />

* Configure storage - Default<img width="1917" height="1015" alt="Screenshot 2026-06-30 221526" src="https://github.com/user-attachments/assets/38d7d807-3fec-4eb1-8b76-eca27d071eac" />

* Installed Apache Web Server using User Data<img width="1917" height="1015" alt="Screenshot 2026-06-30 221652" src="https://github.com/user-attachments/assets/b09b947c-0b60-427b-99be-4a408bda585b" />

* User Data Script<img width="1912" height="346" alt="Screenshot 2026-06-30 224413" src="https://github.com/user-attachments/assets/d12b9b67-604f-4fb4-ae2c-bb23fe1e2f15" />

* Running EC2 Instance<img width="1918" height="1015" alt="Screenshot 2026-06-30 221842" src="https://github.com/user-attachments/assets/8f7f7e09-25b8-4b7b-b48e-72922575eebe" />

* Browser displaying Server Details<img width="1918" height="1017" alt="Screenshot 2026-06-30 225051" src="https://github.com/user-attachments/assets/590358c0-d47b-4b97-85c1-f7d37aeb34be" />

---

# Conclusion

Amazon EC2 provides scalable virtual servers in the cloud and enables users to deploy applications quickly. By using User Data scripts and Apache Web Server, a webpage displaying server details was successfully hosted on the EC2 instance.
