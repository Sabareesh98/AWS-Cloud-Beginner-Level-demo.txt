

# 🚀 Deploying a Highly Available EC2-Based Stabilization System (Multi-AZ)

## 📌 Overview

This project demonstrates how to deploy a **highly available computational/stabilization system** using **Amazon EC2 instances across multiple Availability Zones (AZs)** in the **us-east-1 (N. Virginia)** region.
The setup improves availability by running identical EC2 instances in separate AZs and serving traffic via public access.

The deployment uses:

* **Amazon EC2** for compute
* **Amazon EBS** for high-performance block storage
* **Amazon S3** for object storage (user data script)
* **Security Groups** for HTTP access

---

## 🏗️ Architecture

* Two EC2 instances deployed in **different Availability Zones**
* Each instance runs a web server using **user data**
* **Amazon EBS (gp3)** attached to EC2 for storage
* **Amazon S3** stores the user-data script
* Instances are accessed via **Public DNS**

---

## 🧰 AWS Services Used

| Service         | Purpose                    |
| --------------- | -------------------------- |
| Amazon EC2      | Compute instances          |
| Amazon EBS      | Block storage for EC2      |
| Amazon S3       | Object storage for scripts |
| VPC             | Networking                 |
| Security Groups | Network access control     |

---

## 🌍 Region

```
us-east-1 (N. Virginia)
```

---

## 📂 S3 Configuration

* Bucket name: `cloud-first-steps-*`
* Object: `user-data.txt`

### user-data.txt

* Installs and configures a web server
* Displays instance metadata on **port 80**

---

## ⚙️ EC2 Configuration

### Instance Details

* **AMI**: Amazon Linux 2023 (Kernel 6.1)
* **Instance Type**: `t3.micro`
* **Storage**: 8 GiB gp3 (default)
* **Key Pair**: None (Lab environment)
* **Public Access**: Enabled

---

## 🌐 Networking

* **VPC**: `cloud-first-steps/LabVpc`
* **Subnet**:

  * Instance 1 → `us-east-1a`
  * Instance 2 → `us-east-1b`
* **Security Group**:

  * Name: `Lab-SG`
  * Rule: Allow HTTP (Port 80) from anywhere

⚠️ *Note:* HTTP is publicly accessible. In production, rules should be more restrictive.

---

## 🚀 Deployment Steps

### 1️⃣ Create / Verify S3 Bucket

* Open **Amazon S3**
* Select bucket starting with `cloud-first-steps-`
* Open `user-data.txt` and review contents

---

### 2️⃣ Launch First EC2 Instance

* Name: `webserver01`
* Subnet: `us-east-1a`
* Attach `user-data.txt` in **Advanced → User Data**
* Launch instance

---

### 3️⃣ Verify Web Server

* Copy **Public IPv4 DNS**
* Open browser:

```
http://<public-dns>
```

* Confirm instance metadata is displayed

---

### 4️⃣ Launch Second EC2 Instance

* Repeat same steps
* Choose subnet in **us-east-1b**
* Confirm web page loads successfully

---

## ✅ Expected Outcome

* Two EC2 instances running in **separate AZs**
* Web server accessible via **public DNS**
* Improved **availability and fault tolerance**


---

## 📸 Screenshots (Optional)

Add screenshots here:

* EC2 running instances
* Web page output
* S3 bucket object view

---

## 📘 Learning Outcomes

* Understand EC2 multi-AZ deployment
* Learn S3 object storage basics
* Use user data for automation
* Improve availability using AZs

---

## 🧑‍💻 Author

**Sabareesh AB**
Cloud & DevOps Enthusiast ☁️

---

