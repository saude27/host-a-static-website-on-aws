![Alt text](/Host_a_Static_Website_on_AWS.png)

This project demonstrates how to host a static HTML web application on AWS, utilizing various AWS services and DevOps practices for scalability, reliability, and security.

## Project Overview
The static website is hosted on AWS EC2 instances within a robust infrastructure, leveraging features such as VPC configuration, Auto Scaling, Load Balancing, and more. Below is a breakdown of the implemented architecture and configurations.

### Key Features
1. **Virtual Private Cloud (VPC):**
   - Configured a VPC with both public and private subnets spanning two different Availability Zones for high availability and fault tolerance.
2. **Internet Gateway:**
   - Deployed an Internet Gateway to enable connectivity between VPC instances and the wider Internet.
3. **Security Groups:**
   - Established Security Groups as a network firewall mechanism to control inbound and outbound traffic.
4. **Availability Zones:**
   - Utilized two Availability Zones to enhance system reliability and fault tolerance.
5. **Public Subnets:**
   - Allocated infrastructure components like the NAT Gateway and Application Load Balancer in Public Subnets.
6. **Private Subnets:**
   - Positioned web servers (EC2 instances) in Private Subnets for enhanced security.
7. **NAT Gateway:**
   - Enabled instances in both private application and data subnets to access the Internet via the NAT Gateway.
8. **EC2 Instances:**
   - Hosted the static website on EC2 instances.
9. **Application Load Balancer (ALB):**
   - Employed an ALB and a target group to distribute web traffic evenly to an Auto Scaling Group of EC2 instances across multiple Availability Zones.
10. **Auto Scaling Group:**
    - Configured an Auto Scaling Group for managing EC2 instances automatically, ensuring availability, scalability, fault tolerance, and elasticity.
11. **Certificate Manager:**
    - Secured application communications using AWS Certificate Manager.
12. **SNS Notifications:**
    - Configured Simple Notification Service (SNS) for alerts regarding activities within the Auto Scaling Group.
13. **Route 53:**
    - Registered the domain name and set up DNS records using Route 53 for easy access.
14. **Version Control:**
    - Stored web files on GitHub for version control and collaboration.

## Architecture Diagram
Refer to the [GitHub repository](https://github.com/aosnotes77/host-a-static-website-on-aws) for the architecture diagram.

## Deployment Instructions
### Prerequisites
- AWS Account with necessary permissions.
- Registered domain name.
- GitHub account.
### Steps
1. **Launch EC2 Instances**
   - Use the provided `User Data` script to automate instance configuration.
2. **User Data Script**
   ```bash
   #!/bin/bash
   sudo su
   yum update -y
   yum install -y httpd
   cd /var/www/html
   yum install git -y
   git clone https://github.com/aosnotes77/host-a-static-website-on-aws.git
   cp -R host-a-static-website-on-aws/. /var/www/html/
   rm -rf host-a-static-website-on-aws
   systemctl enable httpd
   systemctl start httpd
   ```
3. **Configure Load Balancer and Auto Scaling**
   - Set up an Application Load Balancer with a target group pointing to your EC2 instances.
   - Configure Auto Scaling Group to handle traffic spikes.
4. **Configure Domain Name**
   - Use Route 53 to link the domain name to the Load Balancer.
5. **Enable HTTPS**
   - Use AWS Certificate Manager to secure your application with HTTPS.
6. **Set Up Monitoring**
   - Configure SNS to receive notifications about your Auto Scaling Group’s activities.

## Repository
Access the repository containing the reference architecture diagram and deployment scripts: [GitHub Repository](https://github.com/aosnotes77/host-a-static-website-on-aws)

## Contact
For questions or support, feel free to open an issue in the GitHub repository or reach out directly.





