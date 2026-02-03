# AWS-Data-Engineering-Foundations
Build a secure, scalable network foundation where all AWS data services (EC2, RDS, S3 access, CDC tools) will live
## 1. Virtual Private Network
A VPC is basically a private network in AWS that a Data Engineer Controls.
Everything a data engineer deploys: EC2, RDS, EMR, CDC Tools etc have to live within a VPC.

### 1.1 Core Networking Concepts
- CIDR Block: This defines IP address range for your VPC. For example 10.0.0.0/16, it means IPs from 10.0.0.0 → 10.0.255.255. This is also a private network.
- Subnets: These divide a VPC into  smaller networks to: separate public and private resources, improve security and control routing. On hands-on, we shall create a public subnet for EC2 and a private network for RDS.
- Public Subnet: This has: internet access, EC2 lives here and has Internet Gateway (IGW) route.
- Private Subnet: This has no internet access, RDS lives here and has no IGW route.
- Internet Gateway (IGW): This allows traffic between VPC and internet, it must be attached to a VPC,and it works only if route tables allow it. Therefore, No IGW = no internet access
- Route Tables: They decide where traffic goes. For example, 0.0.0.0/0 → Internet Gateway means Any traffic not local → send to internet.

### 1.2 Hands-On: Create A VPC

  
