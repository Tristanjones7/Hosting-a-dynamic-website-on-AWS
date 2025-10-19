<h1 align="center">🌐 Dynamic Website Hosting on AWS</h1>
<p align="center">
A secure, scalable, and production-grade deployment of a <b>dynamic web application</b> on AWS — leveraging infrastructure-as-code and cloud-native best practices.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/AWS-Terraform-orange?logo=amazonaws&logoColor=white" alt="AWS Terraform Badge"/>
  <img src="https://img.shields.io/badge/Infrastructure-as-Code-blue?logo=terraform&logoColor=white" alt="IaC Badge"/>
  <img src="https://img.shields.io/badge/Automation-Flyway-red?logo=flyway&logoColor=white" alt="Flyway Badge"/>
  <img src="https://img.shields.io/badge/Load%20Balancing-ALB-green?logo=aws&logoColor=white" alt="ALB Badge"/>
</p>

---

## 🧱 Architecture Overview

Built within a custom **VPC**, this setup spans **public and private subnets** across two Availability Zones for high availability and security.  
It integrates the following key AWS components:

- **Amazon EC2** — hosts the dynamic web app in private subnets  
- **Amazon RDS (MySQL)** — backend database for application data  
- **Amazon S3** — stores Flyway SQL migration files  
- **Flyway** — automates database schema deployment  
- **Application Load Balancer (ALB)** — distributes traffic across EC2s  
- **Target Groups** — enable routing and health checks  
- **Auto Scaling Group (ASG)** — ensures instance scalability and availability  
- **AWS Certificate Manager (ACM)** — manages SSL/TLS certificates  
- **Amazon Route 53** — handles DNS and domain routing  
- **NAT Gateway** + **EC2 Instance Connect Endpoint** — secure outbound internet access  
- **Security Groups** — manage network ingress and egress rules  
- **IAM Roles & Policies** — enforce least-privilege permissions  

---

## 📐 Architecture Diagram

<p align="center">
  <img src="./Docs/architecture-diagram.png" alt="Architecture Diagram" width="700">
</p>

### 🧩 Mermaid Architecture Diagram

```mermaid
graph TD
    A[User] -->|HTTPS| B[Route 53]
    B --> C[Application Load Balancer]
    C --> D[EC2 Auto Scaling Group]
    D --> E[(Amazon EFS)]
    D --> F[(Amazon RDS)]
    C --> G[Internet Gateway]
    G --> H[NAT Gateway]
    H --> D
    D --> I[Private Subnets]
    C --> J[Public Subnets]
    C --> K[ACM SSL Certificates]
    D --> L[S3 Bucket (SQL Files)]
    D --> M[Flyway Migrations]
    D --> N[Security Groups]

    subgraph VPC
        J
        I
        E
        F
        L
    end
🌍 Live Site Preview
<p align="center"> <img src="./image.png" alt="Live Website Screenshot" width="700"> </p>
🚀 Deployment Workflow
Launch EC2 instances via Auto Scaling Group (ASG) within private subnets
On startup, EC2 pulls SQL migration scripts from S3
Flyway applies migrations to the RDS MySQL database
The ALB routes incoming HTTPS traffic to healthy EC2s
ACM issues and manages the SSL certificate
Route 53 connects the domain to the ALB for public access
📸 Screenshots
✅ Website via Application Load Balancer


✅ EC2 Instances (Auto Scaling Group)


✅ Application Load Balancer


✅ Target Group Health Checks


✅ RDS Instance


✅ S3 Bucket (Flyway SQL Files)


🧪 Tools & Services Used
Service	Purpose
EC2	Host web server
RDS MySQL	Relational database backend
ALB	Load balancing & SSL termination
ASG	Scaling and resilience
Route 53	Domain & DNS routing
ACM	HTTPS encryption
S3	SQL migration storage
Flyway	Database automation
NAT Gateway	Outbound internet access
EC2 ICE	Secure shell connectivity
Security Groups	Access control
IAM	Role-based permissions
🧹 Post-Deployment Cleanup
To stay within the AWS Free Tier, all cost-incurring resources were decommissioned after testing:
✅ NAT Gateway deleted
✅ EC2 & ASG terminated
✅ ALB and Target Groups removed
✅ RDS instance deleted
✅ EBS volumes cleaned

💼 About the Author
Tristan Jones
AWS Certified Solutions Architect – Associate
🚀 Aspiring Cloud Engineer building production-ready AWS projects.
🔗 LinkedIn
💻 GitHub
📬 Contributing
Contributions are welcome — open an issue or PR with your improvements and ideas!
📄 License
This project is open source under the MIT License.
