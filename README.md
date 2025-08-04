## 📐 Architecture Overview

This project follows a **3-tier design** consisting of:

- **Presentation Tier (Web Tier)** – WordPress on EC2 behind an ALB with Auto Scaling.
- **Application Tier** – Business logic handled within the WordPress EC2 instances.
- **Data Tier** – RDS MySQL hosted in private subnets with no public access.

- ## 🔧 AWS Services Used

| Service         | Purpose                                                   |
|----------------|-----------------------------------------------------------|
| VPC             | Isolated network with public/private subnets             |
| EC2             | Hosts WordPress with Apache/Nginx                        |
| RDS (MySQL)     | Managed relational database in private subnet            |
| ALB             | Distributes traffic to EC2s in multiple AZs              |
| Auto Scaling    | Ensures high availability and scale-out for EC2 tier     |
| Route 53        | Domain name routing                                      |
| CloudFront      | CDN for caching and SSL termination                      |
| S3              | Stores static content and backups                        |
| IAM             | Role-based secure access                                 |
| CloudWatch      | Logs, alarms, and metrics                                |
| CloudTrail      | Auditing and tracking API calls                          |
| Security Groups | Fine-grained instance-level firewall                     |

---

## 💸 Cost Estimation

Estimated Monthly Cost (light usage):

| Resource      | Type                    | Cost Estimate (₹) |
|---------------|-------------------------|--------------------|
| EC2 (t2.micro) | Free Tier eligible      | ₹0                 |
| RDS (db.t3.micro) | Pay-as-you-go       | ₹800 - ₹1200       |
| S3             | Low GBs of storage      | ₹50 - ₹100         |
| CloudFront     | Light CDN usage         | ₹100 - ₹200        |
| Route 53       | Hosted zone + queries   | ₹70 - ₹120         |

> 💡 Tip: Use budgets, alarms, and auto-stop scripts to control cost.

---

## 📖 Lessons Learned

- Hands-on experience managing public/private subnets and route tables.
- Learned how to securely place the DB in private subnet.
- Faced and solved ALB health check failures using logs and tuning.
- Understood the manual orchestration of AWS services.
- IAM role assignment was key to secure automation without exposing credentials.

---

## 🚀 How to Deploy

1. Create a **custom VPC** with 2 public and 2 private subnets across 2 AZs.
2. Deploy **EC2 instances** in public subnets and set up WordPress.
3. Set up **RDS MySQL** in private subnets.
4. Configure **ALB** and **Auto Scaling Group** for EC2.
5. Point **Route 53** to **ALB DNS** and attach SSL via CloudFront (optional).
6. Secure with IAM roles, SGs, and enable **CloudWatch Logs + Alarms**.
7. Upload static assets to **S3**, optionally serve via CloudFront.

## 📈 Future Enhancements

- [ ] Migrate to **Terraform** or **CloudFormation**
- [ ] Add CI/CD with GitHub Actions
- [ ] Integrate AWS WAF and Shield for security
- [ ] Containerize with ECS or EKS for microservices
- [ ] Monitoring dashboards using Grafana + CloudWatch metrics

---

## 🧠 Author Info

**Nawaz Kapadia**  
🎯 Passionate Cloud Engineer | Hands-On Infra Builder  


---

> 🌟 *Feel free to fork, clone, or connect! Let’s build the cloud together.*
