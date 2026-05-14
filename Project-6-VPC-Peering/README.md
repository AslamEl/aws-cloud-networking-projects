# 🔗 Project 6 – VPC Peering

This project focuses on connecting two separate Virtual Private Clouds (VPCs) using a **VPC peering connection** – allowing them to communicate privately using internal IP addresses, as if they were on the same network, without going through the public internet.

---

## ✅ What I Accomplished

- **Created two VPCs** (NextWork-1 with CIDR `10.1.0.0/16` and NextWork-2 with CIDR `10.2.0.0/16`) using the VPC wizard  
- **Set up a VPC peering connection** between the two VPCs (requester → accepter)  
- **Updated route tables** on both VPCs to direct traffic destined for the other VPC’s CIDR block across the peering connection  
- **Launched EC2 instances** in each VPC (using EC2 Instance Connect, no key pairs needed)  
- **Troubleshot connectivity issues** – added an Elastic IP to Instance 1, and fixed security group ICMP rules to allow `ping` across the peering link  
- **Successfully tested VPC peering** by pinging from Instance 1 (VPC 1) to Instance 2’s private IP address

---

## 🧩 Architecture Diagram

Below is the multi‑VPC architecture I built – two VPCs, each with one public subnet, connected via a VPC peering link:

![VPC Peering Architecture](./Documents/VPC-Peering.png)

---

## 📄 Documentation

Full step‑by‑step instructions, peering setup, route table updates, Elastic IP allocation, security group fixes, and ping test results are documented here:  
[📥 Project 6 – VPC Peering (PDF)](./Documents/VPC-Peering.pdf)

---

## 🌟 Key Learnings

> This project showed me that connecting two VPCs is more than just creating a peering link – route tables and security groups must be explicitly updated to allow traffic to flow.

- **Unique CIDR blocks are essential** – Overlapping IP ranges cause routing conflicts; VPCs in a peering relationship must have non‑overlapping CIDRs.  
- **VPC peering connection** – A direct, private link between two VPCs using internal AWS network (not the public internet).  
- **Requester vs Accepter** – The VPC that initiates the peering is the requester; the other must accept the invitation.  
- **Route table updates** – Even after the peering connection is active, each VPC needs a route entry (destination = other VPC’s CIDR, target = peering connection) to actually send traffic across.  
- **Elastic IP** – Required when an instance in a public subnet doesn’t automatically get a public IPv4 address; Elastic IP provides a static public address for internet access (e.g., EC2 Instance Connect).  
- **Security groups block ICMP by default** – To allow `ping` across a peering connection, add an inbound ICMP (type 8, code 0) rule for the other VPC’s CIDR.  
- **EC2 Instance Connect** – Works without key pairs, but the instance needs a public IP (or Elastic IP) and inbound SSH (port 22) from the Instance Connect IP range.

---

## 🛠️ Commands I Used

```bash
# From Instance 1 (in VPC 1) to Instance 2 (in VPC 2)
ping <private-ip-of-instance-2>   # e.g., ping 10.2.0.123

# Expected result: replies from Instance 2 confirming peering works
```
## 🙏 Credits

Big thanks to **NextWork** for providing this hands‑on, real‑world project.  
Explore more [here](https://link.nextwork.org/linkedin)

---

## 🔖 Tags

`#AWS` `#CloudComputing` `#AmazonVPC` `#EC2` `#Networking`  
`#SecurityGroups` `#PublicSubnet` `#VPC Peering` `#NextWork`
