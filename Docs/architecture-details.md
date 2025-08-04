
---

## 🧱 Core Components

### 🔹 VPC & Networking
- Custom VPC (`10.0.0.0/16`)
- 2 Public subnets (Web/ALB)
- 2 Private subnets (App/RDS)
- Internet Gateway (for public traffic)
- NAT Gateway (to allow outbound from private subnets)
- Route Tables (Public + Private)
- Security Groups and NACLs

### 🔹 Web Tier (Public)
- EC2 instances running Apache + PHP + WordPress
- Auto Scaling Group across 2 AZs
- Application Load Balancer for routing traffic
- Connected to Route 53 (DNS) or CloudFront (CDN)

### 🔹 Application Tier (Private) – Optional
- EC2 instances to handle PHP-FPM or business logic
- Only accessible by Web Tier

### 🔹 Database Tier (Private)
- Amazon RDS MySQL (Multi-AZ for HA)
- Automatic backups, failover
- Security Group allows access only from App Tier

---

## 🛠️ Services Used

| Service       | Purpose                                      |
|---------------|----------------------------------------------|
| VPC           | Network isolation and architecture foundation|
| EC2           | Web & (optionally) App servers               |
| ALB           | Load balancing and health checks             |
| ASG           | Auto scaling based on load                   |
| RDS           | Managed MySQL database                       |
| CloudWatch    | Logs, metrics, alarms                        |
| IAM           | Access control for EC2 and other services    |
| S3            | Optional: for media storage or backups       |
| CloudTrail    | Audit logs of all activity                   |
| Route 53      | DNS management                               |
| CloudFront    | (Optional) CDN for global delivery           |

---

## 🚦 Security Considerations

- Public subnets only expose Load Balancer and web servers
- Private subnets restrict database access
- EC2 IAM roles grant minimal access (e.g., S3, CloudWatch)
- Encrypted RDS, Key Pair authentication for EC2
- CloudTrail enabled for audit logging
- HTTPS via ALB + ACM (optional for SSL termination)

---

## 📡 High Availability & Scaling

- Multi-AZ deployment for Web Tier and RDS
- Health checks on ALB ensure faulty instances are replaced
- ASG scales EC2 up/down based on CPU thresholds
- RDS has automated failover across AZs

---

## 📈 Monitoring & Logging

- **CloudWatch Alarms**: High CPU usage triggers scaling
- **CloudWatch Logs**: System and app logs stored
- **CloudTrail**: Tracks API activity for auditing

---

## 🚀 Deployment Strategy

1. Create VPC, subnets, route tables, and gateways
2. Launch ALB and configure target groups
3. Deploy EC2 web instances and register with ALB
4. Set up ASG with launch templates
5. Launch RDS in private subnets with security group
6. Configure WordPress and connect to RDS
7. Add DNS (Route 53) or CDN (CloudFront)
8. Enable CloudWatch, IAM roles, CloudTrail

---

## 💬 Notes

- WordPress installed manually from ALB DNS
- No Terraform or IaC – setup done entirely through AWS Console
- Architecture supports extension to ECS/EKS or CI/CD in future

---

## 🧭 Future Enhancements

- Add WAF to ALB for security
- Move app tier to containers (ECS or EKS)
- Automate provisioning using Terraform
- Setup CI/CD pipeline (e.g., GitHub Actions + CodeDeploy)
- Enable S3 versioning for backups
- Introduce SQS to decouple services

---

**Made with 💻 and ☁️ by Nawaz**

