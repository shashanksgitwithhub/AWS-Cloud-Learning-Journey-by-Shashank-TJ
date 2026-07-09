<p align="center">
  <img src="https://img.shields.io/badge/AWS-Load Balancer-orange" alt="AWS Badge">
</p>

# ☁ Day 08 - Application Load Balancer (ALB)

## Objective

To understand the concept of Load Balancing and learn how to create an Application Load Balancer (ALB) to distribute incoming traffic across multiple EC2 instances.

---

# What is a Load Balancer?

A Load Balancer is a service that automatically distributes incoming client requests across multiple servers to improve application availability, scalability, and fault tolerance.

Instead of sending all requests to a single server, the Load Balancer intelligently forwards traffic to healthy EC2 instances.

---

# Why Do We Need a Load Balancer?

Without a Load Balancer:

* A single EC2 instance receives all traffic.
* High traffic may cause server overload.
* If the instance fails, the application becomes unavailable.

With a Load Balancer:

* Traffic is distributed evenly.
* High availability is achieved.
* Fault tolerance is improved.
* Better application performance.

---

# Types of AWS Load Balancers

## 1. Application Load Balancer (ALB)

* Operates at Layer 7 (Application Layer)
* Supports HTTP and HTTPS traffic
* Performs content-based routing

Example:

* Routing based on URL path
* Routing based on hostname

---

## 2. Network Load Balancer (NLB)

* Operates at Layer 4 (Transport Layer)
* Supports TCP, UDP, and TLS
* Designed for extremely high performance and low latency

---

## 3. Gateway Load Balancer (GWLB)

* Used for deploying and managing virtual network appliances such as firewalls.

---

# Application Load Balancer Architecture

```text
                    Internet
                        │
                        ▼
            Application Load Balancer
                    │           │
                    ▼           ▼
             EC2 Instance 1  EC2 Instance 2
```

---

# Components of an ALB

## 1. Listener

A process that checks for incoming client requests.

Example:

* HTTP → Port 80
* HTTPS → Port 443

---

## 2. Target Group

A logical group of EC2 instances that receive traffic from the Load Balancer.

The ALB forwards requests only to healthy targets.

---

## 3. Health Checks

The Load Balancer continuously checks whether EC2 instances are healthy.

If an instance becomes unhealthy, traffic is automatically redirected to healthy instances.

---

# Practical Performed

## Step 1: Launch EC2 Instances

Created two Ubuntu EC2 instances.

Example:

* WebServer-1
* WebServer-2

Each instance was configured with Apache Web Server using a User Data script.

---

## Step 2: Verify Web Servers

Access each instance using its Public IP Address and verify that the web page is displayed successfully.

---

## Step 3: Create Target Group

Navigate to:

```text
EC2 → Target Groups
```

Configuration:

* Target Type: Instances
* Protocol: HTTP
* Port: 80

Register:

* WebServer-1
* WebServer-2

---

## Step 4: Create Application Load Balancer

Navigate to:

```text
EC2 → Load Balancers → Create Load Balancer
```

Select:

```text
Application Load Balancer
```

Configuration:

* Internet-facing
* IPv4
* Listener: HTTP (Port 80)

---

## Step 5: Configure Network

Select:

* VPC
* Public Subnets

Attach the Security Group allowing HTTP traffic.

---

## Step 6: Attach Target Group

Select the previously created Target Group.

Complete the Load Balancer creation.

---

## Step 7: Test the Load Balancer

Copy the DNS Name of the Load Balancer.

Example:

```text
http://my-load-balancer-123456.ap-south-1.elb.amazonaws.com
```

Refresh the page multiple times to observe requests being distributed across different EC2 instances.

---

# Key Learnings

* Understood the purpose of Load Balancing.
* Learned the difference between ALB, NLB, and GWLB.
* Created a Target Group.
* Configured an Application Load Balancer.
* Registered EC2 instances with the Target Group.
* Verified traffic distribution between multiple servers.

---

# Interview Questions

### What is a Load Balancer?

A Load Balancer distributes incoming client requests across multiple servers to improve availability and performance.

---

### What is an Application Load Balancer?

An Application Load Balancer (ALB) operates at Layer 7 and distributes HTTP/HTTPS traffic.

---

### What is a Target Group?

A Target Group is a collection of EC2 instances that receive traffic from the Load Balancer.

---

### What is a Health Check?

A Health Check continuously monitors EC2 instances to ensure traffic is sent only to healthy instances.

---

### Difference between ALB and NLB

| Application Load Balancer | Network Load Balancer    |
| ------------------------- | ------------------------ |
| Layer 7                   | Layer 4                  |
| HTTP / HTTPS              | TCP / UDP / TLS          |
| Content-based routing     | High-performance routing |

---

# Screenshots to Add
* Create a VPC<img width="1907" height="1010" alt="Screenshot 2026-07-04 182126" src="https://github.com/user-attachments/assets/cc5a1003-9ef4-484e-8508-cbbe8726fa07" />
* Create internet gateway<img width="1906" height="1006" alt="Screenshot 2026-07-04 182215" src="https://github.com/user-attachments/assets/a0e8bc8c-3fdb-438c-917c-a5d66e16fc99" />
* Attach to VPC<img width="1905" height="1006" alt="Screenshot 2026-07-04 182244" src="https://github.com/user-attachments/assets/2ba1915d-c4e8-42f1-84d8-db54d6021824" />
* Create two subnets<img width="1907" height="1005" alt="Screenshot 2026-07-04 182532" src="https://github.com/user-attachments/assets/1fd398bf-9eac-4813-9ceb-cc2e8a0f1906" />
* Craete route table --> Assosiate subnets --> Edit routes<img width="1907" height="1007" alt="Screenshot 2026-07-04 182607" src="https://github.com/user-attachments/assets/2ad8d533-e511-41b9-8c78-f00b1e86eb7a" />
  <img width="1907" height="1007" alt="Screenshot 2026-07-04 182628" src="https://github.com/user-attachments/assets/a72bc5f1-935f-4d92-9eaa-2cb6e04a0b32" />
  <img width="1905" height="1012" alt="Screenshot 2026-07-04 182700" src="https://github.com/user-attachments/assets/9db8c6ef-45ec-4a30-8213-55f32cb29cdd" />
* Launch two EC2 instances<img width="1905" height="1009" alt="Screenshot 2026-07-04 185203" src="https://github.com/user-attachments/assets/bdfcd023-b86c-46a2-b638-8c13958af105" />
* Target Group Configuration<img width="1907" height="1013" alt="Screenshot 2026-07-04 184132" src="https://github.com/user-attachments/assets/f8e8bb4a-aa29-4f00-ac3d-b4d9332d31ac" />
  <img width="1907" height="1012" alt="Screenshot 2026-07-04 184155" src="https://github.com/user-attachments/assets/72d553eb-3d77-4586-ac13-325ab6d65f20" />
  <img width="1906" height="1014" alt="Screenshot 2026-07-04 184213" src="https://github.com/user-attachments/assets/d2033e84-7f87-4f11-9d86-3af647912b04" /> 
* Registered Targets<img width="1907" height="1009" alt="Screenshot 2026-07-04 184225" src="https://github.com/user-attachments/assets/1ff95ff0-b2ca-43b6-b9af-57addabf601d" />
  <img width="1905" height="1007" alt="Screenshot 2026-07-04 184305" src="https://github.com/user-attachments/assets/0ec173ce-8439-4fc1-9c19-26fef9a9536d" />
  <img width="1906" height="1007" alt="Screenshot 2026-07-04 184323" src="https://github.com/user-attachments/assets/22fb56b6-4835-4fb4-bf00-de17dffe6293" />
* Application Load Balancer Configuration<img width="1907" height="1010" alt="Screenshot 2026-07-04 184402" src="https://github.com/user-attachments/assets/191fd582-ed1c-4281-a5ff-e93ae87717a8" />
  <img width="1907" height="1011" alt="Screenshot 2026-07-04 184424" src="https://github.com/user-attachments/assets/e31fce75-ebdf-4929-9add-b2e84b32cd60" />
  <img width="1907" height="1007" alt="Screenshot 2026-07-04 184445" src="https://github.com/user-attachments/assets/512e489e-d752-461c-9fdb-4347b40bfd99" />
  <img width="1906" height="1010" alt="Screenshot 2026-07-04 184544" src="https://github.com/user-attachments/assets/e123b53f-5d3e-4852-8ca4-14fc6ad1e686" />
  <img width="1906" height="1013" alt="Screenshot 2026-07-04 184556" src="https://github.com/user-attachments/assets/79c406ea-7116-4a9b-8cb6-fc46eb5f24d7" />
  <img width="1907" height="1012" alt="Screenshot 2026-07-04 184613" src="https://github.com/user-attachments/assets/2f9198d6-c7bc-48fa-a450-01c982e1e94e" />
  <img width="1907" height="1006" alt="Screenshot 2026-07-04 184634" src="https://github.com/user-attachments/assets/7357db69-454a-477e-b662-b5dc856a1a2b" />
  <img width="1907" height="1006" alt="Screenshot 2026-07-04 184651" src="https://github.com/user-attachments/assets/04d4b37d-d3c3-447a-a902-4be01c7f2876" />
  <img width="1907" height="1012" alt="Screenshot 2026-07-04 184738" src="https://github.com/user-attachments/assets/06b64ee5-9dfd-4dd2-92cd-2e451d1cd563" />
  <img width="1907" height="1009" alt="Screenshot 2026-07-04 185043" src="https://github.com/user-attachments/assets/062566f1-d74f-4b7e-b576-b1190bc9e2b0" />
* Load Balancer DNS Name<img width="1530" height="102" alt="Screenshot 2026-07-04 185245" src="https://github.com/user-attachments/assets/251997f7-8e77-48bb-a331-833ba2007df7" />
* Browser displaying the hosted application<img width="1905" height="1004" alt="Screenshot 2026-07-04 185350" src="https://github.com/user-attachments/assets/cfc924a6-22bc-4220-9379-83b496140260" />
  <img width="1907" height="1011" alt="Screenshot 2026-07-04 185404" src="https://github.com/user-attachments/assets/72e2006c-8c94-460f-96f6-b868dff5e9a6" />

---

# Conclusion

Successfully created an Application Load Balancer (ALB), configured a Target Group, registered multiple EC2 instances, and verified traffic distribution across healthy servers. This implementation improves application availability, scalability, and fault tolerance.
