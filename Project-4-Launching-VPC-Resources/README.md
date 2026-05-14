# 🚀 Project 4 – Launching VPC & EC2 Instances (Public + Private)

This project focuses on building a secure, two‑tier cloud network inside AWS — a custom **Virtual Private Cloud (VPC)** with both public and private subnets, plus EC2 instances that demonstrate controlled internet access and internal communication.

---

## ✅ What I Accomplished

- **Created a custom VPC** with public and private subnets, an Internet Gateway, route tables, security groups, and network ACLs  
- **Launched a public EC2 instance** (reachable from the internet via SSH/HTTP)  
- **Launched a private EC2 instance** (hidden from the internet, only accessible from the public instance)  
- **Set up security group rules** so only the public instance can SSH into the private one  
- **Used the VPC wizard** to quickly create a second VPC with automatic subnet, route table, and gateway configuration  
- **Explored VPC resource maps**, CIDR block planning, NAT gateway costs, and high‑availability design (0 or 2 public subnets)

---

## 🧩 Architecture Diagram

Here’s how my custom VPC is structured — public instance in a public subnet (with IGW), private instance in a private subnet, and security group rules controlling traffic:

![VPC with Public & Private Subnets](./Documents/launching-vpc-resources.png)

> *(Placeholder — replace with your own diagram or CLI visual)*

---

## 📄 Documentation

Full step‑by‑step instructions, CLI commands, security group configurations, and screenshots are available here:  
[📥 Project 4 – VPC & EC2 Setup Documentation (PDF)](./Documents/launching-vpc-resources.pdf)

---

## 🌟 Key Learnings

> This project taught me how to build a realistic, secure cloud network — not just a flat VPC, but one with separation between public‑facing and private resources.

- **CIDR block isolation** – Two VPCs can share the same CIDR (e.g., `10.0.0.0/16`) without conflict because they are isolated by default.  
- **Security group chaining** – A private server’s security group can reference a public security group as its source, allowing controlled access.  
- **Public vs private subnets** – Public subnets have an Internet Gateway route; private subnets don’t.  
- **NAT gateway trade‑offs** – NAT gateways let private instances reach the internet (for updates) but cost money; for this project I chose “None”.  
- **High availability design** – The VPC wizard forces 0 or 2 public subnets — never 1 — to ensure redundancy across Availability Zones.  
- **Key pair & SSH** – Used `.pem` private keys for secure, password‑less login to EC2 instances.  
- **VPC Resource Map** – A visual tool that shows how subnets, route tables, gateways, and NACLs are connected.

---

## 🙏 Credits

Big thanks to **NextWork** for providing this hands‑on, real‑world project.  
Explore more [here](https://link.nextwork.org/linkedin)

---

## 🔖 Tags

`#AWS` `#CloudComputing` `#AmazonVPC` `#EC2` `#Networking`  
`#SecurityGroups` `#PublicSubnet` `#PrivateSubnet` `#NextWork`
