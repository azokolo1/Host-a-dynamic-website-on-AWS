# Dynamic Website on AWS with Flyway and RDS Migration

This project demonstrates the deployment of a dynamic website on AWS, utilizing a robust and scalable architecture. The solution leverages various AWS services, including EC2, RDS, VPC, Application Load Balancer, Auto Scaling, and more. Additionally, Flyway is used to manage SQL data migrations to Amazon RDS. The project includes deployment scripts and a reference architecture diagram, all available in this GitHub repository.

## Table of Contents
- [Architecture Overview](#architecture-overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [AWS Services Used](#aws-services-used)
- [Deployment Prerequisites](#deployment-prerequisites)
- [Deployment Steps](#deployment-steps)
- [Database Migration with Flyway](#database-migration-with-flyway)
- [Domain and DNS Setup](#domain-and-dns-setup)
- [Security Considerations](#security-considerations)
- [Auto Scaling and Monitoring](#auto-scaling-and-monitoring)
- [Cost Considerations](#cost-considerations)
- [Repository Structure](#repository-structure)
- [Contributing](#contributing)
- [License](#license)

---

## Architecture Overview
The deployment architecture follows best practices for high availability, security, and scalability:
- Multi-AZ (Availability Zone) deployment for fault tolerance.
- Virtual Private Cloud (VPC) with public and private subnets.
- Secure connections through EC2 Instance Connect Endpoint.
- Load balancing and auto-scaling to handle varying traffic loads.
- Data migration and version control using Flyway.

The architecture diagram is available in the repository.

---

## Features
- Highly available and scalable dynamic website.
- Secure access to EC2 instances using Instance Connect Endpoint.
- Automated scaling and load balancing.
- SSL/TLS security for application communications using Certificate Manager.
- Data migration to Amazon RDS with Flyway.
- Centralized alerting with Amazon SNS.
- Domain registration and DNS management with Route 53.
- Application code storage in S3 for efficient deployment.

---

## Tech Stack
- **Backend:** EC2 Instances (Amazon Linux/Ubuntu)
- **Database:** Amazon RDS (SQL-based database)
- **Infrastructure as Code (IaC):** Terraform (based on deployment scripts)

---

## AWS Services Used
- **VPC (Virtual Private Cloud):** For isolated networking.
- **Subnets:** Public and private subnets across multiple AZs.
- **Internet Gateway:** To enable internet connectivity.
- **NAT Gateway:** For secure outbound traffic from private subnets.
- **EC2 Instances:** Hosting the web application.
- **Application Load Balancer:** Distributing traffic across multiple EC2 instances.
- **Auto Scaling Group:** Managing the number of running EC2 instances.
- **Certificate Manager:** For SSL/TLS certificates.
- **SNS (Simple Notification Service):** For Auto Scaling alerts.
- **Route 53:** Domain registration and DNS management.
- **S3:** Storage for application codes and web files.
- **RDS (Relational Database Service):** Managed SQL database.
- **Flyway:** Database migration tool.

---

## Deployment Prerequisites
- An AWS account with necessary permissions.
- Registered domain name.
- Configured AWS CLI on your local machine.
- SSH key pair for EC2 access.
- Flyway installed locally for database migrations.
- GitHub repository cloned locally.

---

## Deployment Steps
1. **Clone the Repository:**
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. **Create the Infrastructure:**
   - Use the deployment scripts in the repository to set up the infrastructure. 
   - Choose either CloudFormation or Terraform as per your preference.

3. **Deploy the Application:**
   - Upload the application code to the S3 bucket.
   - Launch the EC2 instances from the Auto Scaling Group.
   - Configure the Application Load Balancer to route traffic.

4. **Configure DNS:**
   - Register the domain name using Route 53.
   - Set up DNS records to point to the Application Load Balancer.

---

## Database Migration with Flyway
- Flyway is used for version-controlled database migrations.
- Migration scripts are located in the `/migrations` directory.
- Run the migrations using:
  ```bash
  flyway -configFiles=flyway.conf migrate
  ```

---

## Domain and DNS Setup
- Domain registration is done via Route 53.
- Create A and CNAME records to route traffic to the Application Load Balancer.
- SSL/TLS is managed using AWS Certificate Manager for HTTPS.

---

## Security Considerations
- Security Groups are configured to restrict inbound and outbound traffic.
- EC2 instances are within private subnets for enhanced security.
- Instance Connect Endpoint is used for secure SSH access.

---

## Auto Scaling and Monitoring
- Auto Scaling Group ensures high availability and elasticity.
- SNS is configured to alert on scaling events and other critical activities.
- CloudWatch is used for monitoring metrics and setting alarms.

---

## Cost Considerations
- Costs include EC2 instances, NAT Gateway, RDS, Route 53, and S3 storage.
- Utilize the AWS Pricing Calculator to estimate expenses.
- Use Auto Scaling effectively to minimize costs during low traffic periods.
