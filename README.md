# 🌐 Dynamic Website Hosting on AWS

This project demonstrates the deployment of a secure, scalable, and highly available **dynamic web application** on AWS — using production-grade services and automated infrastructure management.

---

## 🧱 Architecture Overview

The infrastructure is built within a custom VPC, using public and private subnets across two Availability Zones. It leverages the following AWS services:

- **Amazon EC2** (in private subnets) for hosting the application
- **Amazon RDS** (MySQL) as the backend relational database
- **Amazon S3** for storing Flyway SQL migration scripts
- **Flyway** for automated database schema migrations
- **Application Load Balancer (ALB)** for distributing traffic across EC2
- **Target Groups** for EC2 routing and health checks
- **Auto Scaling Group (ASG)** to maintain instance availability and scale based on demand
- **AWS Certificate Manager (ACM)** to manage SSL/TLS certificates for HTTPS
- **Amazon Route 53** for DNS routing and custom domain mapping
- **NAT Gateway** + **EC2 Instance Connect Endpoint** for secure internet access to private resources
- **Security Groups** for fine-grained traffic control
- **IAM roles and policies** to enforce least-privilege access

---

## 📐 Architecture Diagram

📌 _Coming Soon: Diagram will be added here_

---

## 🚀 Deployment Process

1. Launch EC2 instances within an **Auto Scaling Group (ASG)** in private subnets
2. On boot, EC2 pulls SQL scripts from **Amazon S3**
3. **Flyway** migrates the schema and seeds **RDS MySQL**
4. **Application Load Balancer (ALB)** routes incoming traffic to healthy EC2s
5. **ACM** provides HTTPS encryption (SSL) for the website
6. **Route 53** handles domain name routing to the ALB

---

### 📸 Screenshots

#### ✅ Website via Application Load Balancer
![Deployed Website](Docs/Website.png)

#### ✅ EC2 Instances (in Auto Scaling Group)
![EC2 Instances](Docs/EC2Instance.png)

#### ✅ Application Load Balancer
![ALB Dashboard](Docs/ApplicationLoadBalancer.png)

#### ✅ Target Group Health Checks
![Target Group](Docs/TargetGroup.png)

#### ✅ RDS Instance
![RDS Database](Docs/RDSInstance.png)

#### ✅ S3 Bucket (for Flyway SQL files)
![S3 Bucket](Docs/S3-Bucket.png)



---

## 🧪 Tools & Services Used

| Service         | Purpose                           |
|----------------|------------------------------------|
| EC2            | Host web server                    |
| RDS MySQL      | Backend relational database        |
| ALB            | Load balancing and SSL termination |
| ASG            | Auto-healing and scaling instances |
| Route 53       | Domain and DNS routing             |
| ACM            | SSL/TLS for HTTPS                  |
| Target Groups  | Health checks & EC2 linking        |
| S3             | SQL file storage                   |
| Flyway         | DB migration automation            |
| NAT Gateway    | Internet access for private subnet |
| EC2 ICE        | Secure shell access                |
| Security Groups| Network access control             |
| IAM            | Roles and permissions              |

---

## 🧹 Post-Deployment Cleanup

To remain within **AWS Free Tier**, all major cost-incurring services were cleaned up after deployment:

- ✅ NAT Gateway deleted
- ✅ EC2 instances + ASG terminated
- ✅ ALB and Target Groups removed
- ✅ RDS instance deleted
- ✅ EBS volumes cleaned up

---

## 💼 About the Author

**Tristan Jones**  
AWS Certified Solutions Architect – Associate  
🔗 [LinkedIn](https://www.linkedin.com/in/tristan-jones-0a106a217/)  
🚀 Aspiring Cloud Engineer building production-ready AWS projects to launch into the industry.

---

## 📬 Contributing

Contributions and suggestions are welcome!  
Feel free to open an issue or submit a PR with improvements, enhancements, or feature ideas.

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
