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
#### Step 1: In your AWS Console, search VPC and open the VPC Console.
<img width="1536" height="491" alt="image" src="https://github.com/user-attachments/assets/321411e9-7143-4a12-9d0d-4fa25aeab24a" />

On the VPC Console, click on Create VPC.
<img width="1657" height="901" alt="image" src="https://github.com/user-attachments/assets/561439a8-330c-479d-a48e-5afef3df53bb" />

Ensure that you select VPC only.
Then, configure the VPC as follows:
| Setting   | Value                 |
| --------- | -------------------   |
| Name      | `data-platform-vpc-2` |
| IPv4 CIDR | `10.0.0.0/16`         |
| IPv6      | None                  |
| Tenancy   | Default               |


#### Step 2: Create Subnets
Under VPC, navigate to subnets.
<img width="1680" height="270" alt="image" src="https://github.com/user-attachments/assets/576e9aae-1cf9-451c-b34b-43a452c796ce" />

- Public Subnet: Configure it ass follows:
  
| Setting   | Value                 |
| -------   | -------------------   |
| Name      | `public-subnet-2`     |
| VPC       | `data-platform-vpc-2` |
| AZ        | us-east-1c            |
| CIDR      | `10.0.1.0/24`         |


<img width="1680" height="433" alt="image" src="https://github.com/user-attachments/assets/b86f204b-8411-4bdf-805b-abc04dccce0c" />
Start by attaching the VPC we created above.

<img width="1680" height="834" alt="image" src="https://github.com/user-attachments/assets/6f7d020b-7907-49b5-a454-27dc680c30f7" />


- Private Subnets: The procedure is the same as above but, what changes is the CIDR and name.
Configure it as follows:

| Setting | Value                  |
| ------- | -------------------    |
| Name    | `private-subnet-2`     |
| VPC     | `data-platform-vpc-2`  |
| AZ      | us-east-1c             |
| CIDR    | `10.0.2.0/24`          |


<img width="1680" height="834" alt="image" src="https://github.com/user-attachments/assets/aadb3bf8-6549-412d-aaa2-cfd9fdd82483" />



