# 🔌 Project 5 – Testing VPC Connectivity

This project focuses on validating a custom VPC setup by testing connectivity — from your local machine to a public EC2 instance, between public and private instances, and from the public instance to the internet. It reinforces how security groups, network ACLs, route tables, and ICMP rules work together.

---

## ✅ What I Accomplished

- **Connected to a public EC2 instance** using EC2 Instance Connect (and fixed missing SSH inbound rule)  
- **Tested connectivity between public and private instances** using `ping` (and added missing ICMP rules)  
- **Verified internet access from the public instance** using `curl` to confirm route table + Internet Gateway work  
- **Understood the difference between `ping` (ICMP, layer 3) and `curl` (HTTP/TCP, layer 7)**  
- **Troubleshot real‑world blocking issues** – security groups and NACLs that initially prevented SSH, ICMP, and outbound web traffic

---

## 🧩 Architecture Diagram

Below is the connectivity flow I tested – from my laptop → public EC2 (via Instance Connect), from public EC2 → private EC2 (via ping), and from public EC2 → internet (via curl):

![VPC Connectivity Testing](./Documents/Testing-VPC-Connectivity.png)


---

## 📄 Documentation

Full step‑by‑step testing procedures, `ping`/`curl` commands, troubleshooting screenshots, and security group/ACL rule changes are documented here:  
[📥 Project 5 – VPC Connectivity Testing (PDF)](./Documents/Testing-VPC-Connectivity.pdf)

---

## 🌟 Key Learnings

> This project taught me that “connectivity” isn’t automatic – it requires deliberate configuration at multiple layers. Debugging failed SSH and failed ping gave me a much deeper understanding of AWS networking.

- **EC2 Instance Connect** – A service that pushes a temporary SSH key; still requires **inbound SSH (port 22)** rule in the security group.  
- **Security groups are stateful** – Outbound ICMP is allowed automatically if inbound ICMP is permitted, but NACLs require explicit rules both directions.  
- **`ping` uses ICMP** – Many security groups block it by default; you must add an **ICMP (IPv4) Echo Request** inbound rule.  
- **`curl` tests real web traffic** – It confirms outbound HTTP/HTTPS works through the Internet Gateway.  
- **Troubleshooting flow** – Check security groups first (most common), then NACLs, then route tables.  
- **Public vs private connectivity** – Private instance cannot be reached from the internet (by design), but can be reached from the public instance within the VPC.

---

## 🛠️ Commands I Used

```bash
# From AWS Console – EC2 Instance Connect (automatic)

# From public instance to private instance
ping <private-ip-address>

# From public instance to internet
curl https://learn.nextwork.org/projects/aws-host-a-website-on-s3\
```
## 🙏 Credits

Big thanks to **NextWork** for providing this hands‑on, real‑world project.  
Explore more [here](https://link.nextwork.org/linkedin)

---

## 🔖 Tags

`#AWS` `#CloudComputing` `#AmazonVPC` `#EC2` `#Networking`  
`#SecurityGroups` `#PublicSubnet` `#PrivateSubnet` `#NextWork`
