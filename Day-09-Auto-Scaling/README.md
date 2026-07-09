<p align="center">
  <img src="https://img.shields.io/badge/AWS-Auto Scaling-orange" alt="AWS Badge">
</p>

# ☁ Day 09 - Amazon EC2 Auto Scaling

## Objective

To understand Amazon EC2 Auto Scaling and learn how to automatically launch or terminate EC2 instances based on application demand.

---

# What is Auto Scaling?

Amazon EC2 Auto Scaling is an AWS service that automatically adjusts the number of EC2 instances based on traffic, demand, or predefined policies.

It helps maintain application availability while reducing infrastructure costs.

---

# Why Do We Need Auto Scaling?

Without Auto Scaling:

* A single EC2 instance may become overloaded during high traffic.
* Resources remain underutilized during low traffic.
* Manual scaling takes time and may lead to downtime.

With Auto Scaling:

* Automatically launches new EC2 instances when demand increases.
* Automatically terminates unnecessary instances when demand decreases.
* Improves application availability.
* Optimizes infrastructure costs.

---

# Components of Auto Scaling

## 1. Launch Template

A Launch Template stores the configuration required to launch EC2 instances.

It includes:

* Amazon Machine Image (AMI)
* Instance Type
* Key Pair
* Security Group
* User Data Script
* Storage Configuration

---

## 2. Auto Scaling Group (ASG)

An Auto Scaling Group manages a collection of EC2 instances.

It ensures that the desired number of healthy instances is always running.

---

## 3. Scaling Policies

Scaling Policies define when Auto Scaling should add or remove EC2 instances.

Examples:

* CPU Utilization
* Network Traffic
* Memory Usage (via CloudWatch Agent)

---

## 4. CloudWatch Alarms

CloudWatch continuously monitors metrics such as CPU utilization.

When a threshold is crossed, it triggers scaling actions.

---

# Auto Scaling Architecture

<img width="772" height="612" alt="AdobeExpressPhotos_d145826c96d844b2aa3676ccf2b2e321_CopyEdited" src="https://github.com/user-attachments/assets/85762858-4919-4059-9fa5-1374956c767d" />

---

# Practical Performed

## Step 1: Create a Launch Template

Navigate to:

EC2 → Launch Templates

Configuration:

* Ubuntu Server AMI
* t2.micro Instance
* Existing Key Pair
* Existing Security Group
* User Data Script

---

## Step 2: Create an Auto Scaling Group

Navigate to:

EC2 → Auto Scaling Groups

Click:

Create Auto Scaling Group

Select the Launch Template.

---

## Step 3: Configure Networking

Select:

* Existing VPC
* Public Subnets

---

## Step 4: Attach Load Balancer

Choose:

* Attach to an Existing Load Balancer

Select:

* Application Load Balancer

Select the Target Group created previously.

---

## Step 5: Configure Group Size

Example:

Minimum Capacity:

1

Desired Capacity:

2

Maximum Capacity:

4

---

## Step 6: Configure Scaling Policy

Example:

Target Tracking Policy

Metric:

Average CPU Utilization

Target Value:

50%

This means:

* Launch a new EC2 instance when CPU utilization exceeds approximately 50%.
* Terminate unnecessary instances when utilization decreases.

---

## Step 7: Review and Create

Verify all configurations and create the Auto Scaling Group.

---

# Practical Outcome

✅ Created a Launch Template.

✅ Created an Auto Scaling Group.

✅ Attached the Auto Scaling Group to an Application Load Balancer.

✅ Configured scaling policies.

✅ Learned how AWS automatically manages EC2 instances based on demand.

---

# Advantages of Auto Scaling

* High Availability
* Automatic Scaling
* Fault Tolerance
* Cost Optimization
* Improved Performance
* Reduced Manual Intervention

---

# Key Learnings

* Understood the purpose of Auto Scaling.
* Learned the role of Launch Templates.
* Created an Auto Scaling Group.
* Configured scaling policies.
* Integrated Auto Scaling with an Application Load Balancer.

---

# Interview Questions

### What is Amazon EC2 Auto Scaling?

Amazon EC2 Auto Scaling automatically adjusts the number of EC2 instances based on application demand.

---

### What is a Launch Template?

A Launch Template contains the configuration required to launch EC2 instances.

---

### What is an Auto Scaling Group?

An Auto Scaling Group manages a collection of EC2 instances and maintains the desired number of healthy instances.

---

### What is the difference between Desired, Minimum, and Maximum Capacity?

Minimum Capacity:
The minimum number of EC2 instances that must always remain running.

Desired Capacity:
The preferred number of running EC2 instances.

Maximum Capacity:
The maximum number of EC2 instances that Auto Scaling can launch.

---

### Which AWS service triggers Auto Scaling?

Amazon CloudWatch.

---

### Can Auto Scaling work without a Load Balancer?

Yes. However, it is commonly used with an Application Load Balancer to distribute traffic across automatically managed instances.

---

# Screenshots to Add

* Launch Template Creation
* Launch Template Details
* Auto Scaling Group Creation
* Auto Scaling Group Configuration
* Scaling Policy
* Attached Application Load Balancer
* Target Group Association
* Running EC2 Instances

---

# Conclusion

Successfully created a Launch Template and an Auto Scaling Group, configured automatic scaling policies, and integrated the Auto Scaling Group with an Application Load Balancer. This implementation enables applications to automatically handle changing workloads while maintaining high availability and optimizing infrastructure costs.
