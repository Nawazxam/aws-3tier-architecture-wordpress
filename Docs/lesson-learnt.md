# 📘 Lessons Learned – AWS 3-Tier WordPress Architecture

## 📍 Project Overview

This project involved building a scalable, highly available 3-tier architecture for hosting a WordPress website using **only AWS native services** via the AWS Console (no Infrastructure as Code tools). It included EC2, ALB, RDS, Auto Scaling, VPC, Route 53, CloudFront, IAM, CloudWatch, S3, and CloudTrail.

---

## 🚀 Key Lessons Learned

### 1. Manual Setup Deepens Cloud Understanding
- **Hands-on console-based configuration** forced me to learn every component's interconnections deeply.
- Building the network, security groups, and dependencies manually gave me a solid grasp on **cloud architecture fundamentals**.

### 2. Importance of VPC Planning
- Subnet placement (public/private), availability zones, and routing must be **planned in advance**.
- A mistake in subnet mapping or NAT Gateway config can break connectivity for app or DB tiers.

### 3. ALB, ASG & EC2 Coordination
- Learned how **Target Groups** work with ALB and ASG to route traffic reliably.
- Setting up health checks properly was crucial to ensuring **high availability** and **auto-healing**.

### 4. RDS Configuration Matters
- Initially deployed RDS without **public access** — caused connectivity issues with EC2.
- Understood the importance of **subnet group**, **parameter groups**, and **security group access rules**.

### 5. IAM Role Misconfigurations
- Missed attaching roles to EC2 for **S3 or CloudWatch access**, which caused errors until fixed.
- Realized how powerful and dangerous **IAM policies** are when not scoped properly.

### 6. Route 53 and CloudFront Setup
- Mapping domain via Route 53 and integrating it with CloudFront added professionalism and performance.
- Learned about **DNS propagation delays** and **SSL termination via CloudFront**.

### 7. CloudWatch Alarms & Logs Are Vital
- Debugging EC2 and RDS without logs was hard.
- After enabling logs + metrics, I could track performance and **resolve issues proactively**.

### 8. Manual Deployments Are Time-Consuming
- While educational, doing everything manually is **not scalable** or **repeatable**.
- Gained strong motivation to learn **Terraform / CloudFormation** for future projects.

---

## ⚠️ Challenges Faced

| Challenge                          | Resolution                                                                 |
|------------------------------------|----------------------------------------------------------------------------|
| RDS not accessible from EC2        | Updated RDS security group to allow EC2 IP range on port 3306              |
| NAT Gateway costing too much       | Learned to use EC2 NAT instance for budget environments                    |
| Auto Scaling not working properly  | Fixed ALB health checks & attached Launch Template correctly               |
| WordPress not installing correctly | Ensured EC2 had internet + correct PHP/MySQL stack pre-installed           |
| SSL issues with custom domain      | Used AWS Certificate Manager + CloudFront for HTTPS setup                  |

---

## ✅ What I’d Do Differently Next Time

- Use **Terraform** or **CloudFormation** for reproducibility and automation
- Create **Launch Templates with userdata scripts** to bootstrap WordPress dynamically
- Design the architecture using **well-architected principles** from the start
- Implement **CI/CD pipeline** using CodePipeline or GitHub Actions for deployment
- Add **WAF, Shield, and Security Hub** for improved cloud security posture

---

## 🧠 Final Reflection

This project was a powerful deep dive into how cloud infrastructure is manually created and operated. Every small mistake taught me how real-world systems break and how to make them resilient. While it took effort, I now feel much more confident in architecting AWS environments and I’m ready to take on automation using tools like **Terraform** and **Ansible** in the next phase of my journey.

---

**Prepared by Nawaz**  
**Date: August 2025**  
