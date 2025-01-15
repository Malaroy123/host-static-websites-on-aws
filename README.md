# Static Website Hosting on AWS

This repository contains the reference diagram, configuration scripts, and step-by-step instructions for hosting a static HTML web application on AWS. The project utilizes various AWS resources to ensure scalability, security, and high availability.


## **Project Overview/Architecture**

### **1. Virtual Private Cloud (VPC)**
- Configured a VPC with both **public** and **private subnets** across two Availability Zones (AZs) to enhance fault tolerance and reliability.

### **2. Internet Gateway**
- Deployed an Internet Gateway to enable internet connectivity for resources in the VPC’s public subnets.

### **3. Security Groups**
- Established Security Groups as network firewalls to control inbound and outbound traffic for different resources.

### **4. High Availability**
- Leveraged two AZs to distribute resources and improve system reliability.

### **5. Subnet Design**
- **Public Subnets**:
  - Hosted infrastructure components like the **NAT Gateway** and **Application Load Balancer (ALB)**.
- **Private Subnets**:
  - Hosted web servers (EC2 instances) to enhance security.

### **6. EC2 Instance Connect Endpoint**
- Configured for secure, keyless connections to assets within both public and private subnets.

### **7. NAT Gateway**
- Enabled internet access for instances in private subnets through the NAT Gateway.

### **8. Hosting Website on EC2 Instances**
- Deployed a static HTML web application on EC2 instances placed in private subnets.

### **9. Application Load Balancer (ALB)**
- Configured ALB to distribute traffic evenly across an Auto Scaling Group (ASG) of EC2 instances across multiple AZs.

### **10. Auto Scaling Group (ASG)**
- Used ASG to:
  - Automatically scale EC2 instances based on traffic demand.
  - Ensure fault tolerance and elasticity.

### **11. Secure Communications**
- Utilized **AWS Certificate Manager (ACM)** to secure application communications via SSL/TLS certificates.

### **12. Route 53 DNS Configuration**
- Registered a domain name and configured a DNS record in Route 53 for users to access the website with a user-friendly URL.

### **13. Version Control**
- Stored all web files and scripts in GitHub for version control and collaboration.

### **14. Monitoring and Notifications**
- Configured **Amazon SNS** to send alerts for activities within the Auto Scaling Group.


## **Repository Contents**

1. **Reference Diagram**: Visual representation of the architecture.
2. **Configuration Scripts**: Includes scripts for deploying the infrastructure and the website.
3. **Static Web Files**: HTML, CSS, and other assets for the static website.


## **How to Deploy**

### **Prerequisites**
- AWS account with appropriate permissions.
- AWS CLI configured on your local machine.
- Git installed for version control.

### **Deployment Steps**
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/Malaroy123/host-static-websites-on-aws.git
   cd host-static-websites-on-aws

2. **Configure AWS CLI**:
   ```bash
   aws configure

3. **Deploy the Infrastructure**:
- Follow the provided scripts in the repository to set up the VPC, subnets and other resources.

4. **Deploy the Website**:
- SSH into the EC2 instance in the private subnet
- Use the provided deployment sript to set up the Apache HTTP server and host the website.

### Key Features
- Scalability: Auto Scaling ensures that the application can handle traffic spikes.
- High Availability: ALB distributes traffic across multiple AZs.
- Security: Resources are placed in private subnets, and communications are secured with SSL.
- Fault Tolerance: Redundancy is achieved by using multiple AZs.
- Monitoring: Alerts for critical activities ensure timely responses.
