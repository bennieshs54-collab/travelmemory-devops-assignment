# MERN Stack Deployment on AWS using Terraform and Ansible

## Project Overview

This project demonstrates the deployment of a MERN (MongoDB, Express.js, React.js, Node.js) application on AWS using Infrastructure as Code (IaC) with Terraform and Configuration Management using Ansible.

The goal of this project is to automate the provisioning of AWS infrastructure and the deployment of a MERN application while following security best practices.

## Application Used

TravelMemory MERN Application

Repository:
https://github.com/UnpredictablePrashant/TravelMemory

---

# Architecture

```text
Internet
    │
    ▼
Internet Gateway
    │
    ▼
Public Subnet
    │
    ▼
Web Server EC2 Instance
(React Frontend + Node.js Backend)
    │
    ▼
Private Subnet
    │
    ▼
MongoDB EC2 Instance
```

## Components Used

| Component | Purpose |
|------------|----------|
| AWS VPC | Private network for infrastructure |
| Public Subnet | Hosts Web Server |
| Private Subnet | Hosts Database Server |
| Internet Gateway | Internet access for public subnet |
| NAT Gateway | Internet access for private subnet |
| EC2 Web Server | Hosts React and Node.js |
| EC2 Database Server | Hosts MongoDB |
| Security Groups | Firewall and network security |
| IAM Roles | AWS permissions management |
| Terraform | Infrastructure provisioning |
| Ansible | Server configuration and deployment |

---

# Technologies Used

- AWS EC2
- AWS VPC
- AWS IAM
- AWS Security Groups
- Terraform
- Ansible
- MongoDB
- Node.js
- Express.js
- React.js
- Git
- GitHub

---

# Project Structure

```text
mern-devops-assignment/
│
├── terraform/
│   ├── provider.tf
│   ├── vpc.tf
│   ├── subnet.tf
│   ├── internet.tf
│   ├── security.tf
│   ├── ec2.tf
│   ├── outputs.tf
│   └── variables.tf
│
├── ansible/
│   ├── inventory.ini
│   ├── web.yml
│   ├── db.yml
│   └── ansible.cfg
│
├── screenshots/
│   ├── terraform-apply.png
│   ├── vpc.png
│   ├── ec2-instances.png
│   ├── security-groups.png
│   ├── mongodb-running.png
│   └── application-running.png
│
├── README.md
└── .gitignore
```

---

# Infrastructure Provisioning with Terraform

The following AWS resources were created using Terraform:

## Networking

- VPC
- Public Subnet
- Private Subnet
- Internet Gateway
- NAT Gateway
- Route Tables
- Route Table Associations

## Compute Resources

- Web Server EC2 Instance
- Database Server EC2 Instance

## Security

- Security Groups for Web Server
- Security Groups for Database Server

## Identity Management

- IAM Roles
- IAM Instance Profiles

---

# Terraform Workflow

Initialize Terraform:

```bash
terraform init
```

Validate Configuration:

```bash
terraform validate
```

Preview Infrastructure:

```bash
terraform plan
```

Deploy Infrastructure:

```bash
terraform apply
```

Destroy Infrastructure:

```bash
terraform destroy
```

---

# Configuration Management with Ansible

## Web Server Configuration

The Ansible playbook performs the following tasks:

- Updates package repositories
- Installs Git
- Installs Node.js
- Installs npm
- Installs PM2
- Clones the TravelMemory repository
- Installs backend dependencies
- Installs frontend dependencies
- Configures environment variables
- Starts the application

## Database Server Configuration

The Ansible playbook performs the following tasks:

- Installs MongoDB
- Starts MongoDB service
- Enables MongoDB at boot
- Configures MongoDB authentication
- Creates database users
- Creates application database

---

# Application Deployment

## Clone Repository

```bash
git clone https://github.com/UnpredictablePrashant/TravelMemory.git
```

## Backend Setup

```bash
cd backend
npm install
```

Create a `.env` file:

```env
MONGO_URL=mongodb://traveluser:password123@PRIVATE_DB_IP:27017/travelmemory
PORT=5000
```

Start Backend Service:

```bash
pm2 start index.js
```

## Frontend Setup

```bash
cd frontend
npm install
npm start
```

---

# Security Implementation

The following security measures were implemented:

## Network Security

- Web Server deployed in Public Subnet
- MongoDB deployed in Private Subnet
- MongoDB accessible only from Web Server Security Group

## SSH Security

- SSH access restricted to my public IP address
- SSH key-based authentication enabled
- Root login disabled

## Firewall Rules

| Port | Purpose |
|--------|---------|
| 22 | SSH Access |
| 3000 | React Frontend |
| 5000 | Node.js Backend |
| 27017 | MongoDB (Internal Access Only) |

## Additional Hardening

- Disabled Password Authentication
- Configured UFW Firewall
- Restricted MongoDB Access
- Stored secrets in environment variables

---

# Application Workflow

1. User accesses the React frontend through a browser.
2. React frontend sends API requests to the Node.js backend.
3. Node.js backend processes requests.
4. Backend communicates with MongoDB.
5. MongoDB returns data.
6. Backend sends the response back to the frontend.
7. Frontend displays the data to the user.

---

# Screenshots

## Terraform Apply

![Terraform Apply](screenshots/terraform-apply.png)

## AWS VPC

![VPC](screenshots/vpc.png)

## EC2 Instances

![EC2 Instances](screenshots/ec2-instances.png)

## Security Groups

![Security Groups](screenshots/security-groups.png)

## MongoDB Running

![MongoDB Running](screenshots/mongodb-running.png)

## Application Running

![Application Running](screenshots/application-running.png)

---

# Challenges Faced

- Understanding AWS networking concepts such as VPC, subnets, route tables, and NAT Gateway.
- Configuring secure communication between the web server and database server.
- Installing and configuring MongoDB in a private subnet.
- Managing environment variables for backend connectivity.
- Configuring Ansible inventory and SSH access.

---

# Learning Outcomes

Through this project, I learned:

- Infrastructure as Code using Terraform
- AWS Networking and VPC Design
- EC2 Provisioning and Management
- Configuration Management using Ansible
- Secure Deployment of MERN Applications
- MongoDB Administration
- Security Hardening Techniques
- Git and GitHub Workflow

---

# Conclusion

This project successfully demonstrates the deployment of a MERN stack application on AWS using Terraform for infrastructure provisioning and Ansible for configuration management. The deployment follows security best practices by isolating the database in a private subnet and restricting access using security groups and SSH key authentication.

---

# Author

**Name:** Your Name

**USN:** Your USN

**Course:** DevOps / Cloud Computing

**Assignment:** MERN Stack Deployment on AWS using Terraform and Ansible

**GitHub Repository:** https://github.com/yourusername/mern-devops-assignment
"Screenshots"
<img width="940" height="132" alt="image" src="https://github.com/user-attachments/assets/b8fcd771-2a98-43a1-afe3-1ed0af45be8e" />

<img width="940" height="324" alt="image" src="https://github.com/user-attachments/assets/c13ea213-a9d6-472f-8466-655e601154ca" />

<img width="940" height="503" alt="image" src="https://github.com/user-attachments/assets/aff7a293-66ae-4a8c-92e0-2e0af69e0c07" />

<img width="940" height="298" alt="image" src="https://github.com/user-attachments/assets/80a77ab7-02f2-4f71-8570-b520474e3ffe" />

<img width="940" height="82" alt="image" src="https://github.com/user-attachments/assets/ef051826-cad9-45c7-892e-f14f05285ea8" />

<img width="847" height="64" alt="image" src="https://github.com/user-attachments/assets/e511be22-1248-4391-a681-e30748a43018" />

<img width="940" height="425" alt="image" src="https://github.com/user-attachments/assets/a8c73caf-5be1-43d5-b420-82a71a34367e" />

<img width="940" height="243" alt="image" src="https://github.com/user-attachments/assets/0b9bad10-8115-4ad0-bcdc-3de12eef40dd" />

<img width="940" height="395" alt="image" src="https://github.com/user-attachments/assets/a06e6d5d-f4fb-4a56-a84a-67ab207c4a4a" />

<img width="940" height="472" alt="image" src="https://github.com/user-attachments/assets/c630b9ef-46f8-47c2-a68f-dd2666291964" />

<img width="940" height="199" alt="image" src="https://github.com/user-attachments/assets/87762c92-9a2a-4bfb-ad91-208b1bef42ae" />

<img width="940" height="155" alt="image" src="https://github.com/user-attachments/assets/f575a8e6-d2aa-4da0-b70d-17133d05710a" />

<img width="940" height="260" alt="image" src="https://github.com/user-attachments/assets/f338e76c-377f-4b55-8623-9d60bae2c5c9" />

<img width="940" height="587" alt="image" src="https://github.com/user-attachments/assets/e586351f-118d-4111-9e07-52547d354a00" />

<img width="940" height="519" alt="image" src="https://github.com/user-attachments/assets/55ba09f5-7c18-4272-ab89-c0bf45662ac7" />

<img width="940" height="518" alt="image" src="https://github.com/user-attachments/assets/44dd88e6-82ab-4922-9739-10e3c5f1d0ed" />

<img width="940" height="815" alt="image" src="https://github.com/user-attachments/assets/ba404cef-b77f-42fe-a6ad-65b2bfb2d156" />

<img width="940" height="542" alt="image" src="https://github.com/user-attachments/assets/7cb9dcb4-6dec-4047-83bc-f3b3c1bc2ee0" />

<img width="940" height="571" alt="image" src="https://github.com/user-attachments/assets/76ee14df-6ae9-48bb-991d-89963f57c777" />

<img width="940" height="625" alt="image" src="https://github.com/user-attachments/assets/930807e7-1bb2-4b0c-9e06-308e20760bc6" />

<img width="940" height="504" alt="image" src="https://github.com/user-attachments/assets/d39f903f-d570-463f-800f-dee4eca13b6a" />

<img width="940" height="567" alt="image" src="https://github.com/user-attachments/assets/2ae87304-677d-479e-82d1-ff643d9e26f1" />

<img width="940" height="504" alt="image" src="https://github.com/user-attachments/assets/15ac2293-febc-4db2-8868-d7e8d333bbf1" />

<img width="940" height="501" alt="image" src="https://github.com/user-attachments/assets/77f37ff6-9f90-4339-a4ed-61e660f31c19" />

<img width="940" height="229" alt="image" src="https://github.com/user-attachments/assets/3d5f4c25-de32-4a44-b269-2693caa9f7aa" />

<img width="940" height="526" alt="image" src="https://github.com/user-attachments/assets/a12026ef-2f18-4348-b963-e48c0ec432a0" />

<img width="940" height="266" alt="image" src="https://github.com/user-attachments/assets/1b5d5a63-72d9-420e-a836-f17012a19359" />

<img width="940" height="845" alt="image" src="https://github.com/user-attachments/assets/986d704b-bfcf-452d-a048-76f862cbcbf6" />

<img width="940" height="845" alt="image" src="https://github.com/user-attachments/assets/4af1aa1d-cbf7-498a-88e7-fc26458434e6" />

<img width="940" height="168" alt="image" src="https://github.com/user-attachments/assets/e11b34a5-3fb7-49a2-a838-fe175026d5f7" />

<img width="940" height="305" alt="image" src="https://github.com/user-attachments/assets/41d52140-40fb-4195-a859-012781239a0a" />

<img width="940" height="616" alt="image" src="https://github.com/user-attachments/assets/7c8c11dd-7225-4209-9780-30658510258c" />

<img width="940" height="68" alt="image" src="https://github.com/user-attachments/assets/14919146-5707-46a5-9e08-41c7841d5df0" />

<img width="940" height="257" alt="image" src="https://github.com/user-attachments/assets/7dcce9aa-2cba-496f-a0d9-ac94d49cd0d7" />

<img width="940" height="468" alt="image" src="https://github.com/user-attachments/assets/01883bbd-c083-42cd-87f0-2d667ff52af3" />

<img width="940" height="475" alt="image" src="https://github.com/user-attachments/assets/6bfd3145-ef4c-4a86-bbad-12c13bf336b2" />

<img width="940" height="396" alt="image" src="https://github.com/user-attachments/assets/36f7d7a0-7974-4c7a-a62e-2e66af9d3121" />

<img width="940" height="526" alt="image" src="https://github.com/user-attachments/assets/a21e1b0e-dd28-4811-bd00-8d156784a447" />

<img width="940" height="698" alt="image" src="https://github.com/user-attachments/assets/e8099041-4c90-4b21-b749-dbb2030a76cf" />

<img width="940" height="102" alt="image" src="https://github.com/user-attachments/assets/a7fc9aee-89a7-4029-aec0-9b8218d2aa1c" />

<img width="940" height="490" alt="image" src="https://github.com/user-attachments/assets/cad98fdf-2b71-4e82-b56a-76f2c700b867" />

<img width="940" height="532" alt="image" src="https://github.com/user-attachments/assets/20cebb15-9263-42bf-aaf6-dc3c8db67cf0" />

<img width="940" height="502" alt="image" src="https://github.com/user-attachments/assets/68ce8938-60f5-423e-b045-76c064e831f7" />

<img width="940" height="584" alt="image" src="https://github.com/user-attachments/assets/4987bac6-3865-4a62-9ec9-24aacfeaa156" />

<img width="940" height="514" alt="image" src="https://github.com/user-attachments/assets/02f04a19-449a-4ffd-a200-bcbefd54fa3d" />

<img width="940" height="481" alt="image" src="https://github.com/user-attachments/assets/9bcd3feb-dd62-44c6-811e-46056e0d42d6" />

<img width="940" height="701" alt="image" src="https://github.com/user-attachments/assets/ac5f2d4f-d7ba-4627-9448-10cfa44d7676" />

<img width="940" height="522" alt="image" src="https://github.com/user-attachments/assets/7bb1b790-864b-46ff-bc36-4552316edc50" />

<img width="940" height="497" alt="image" src="https://github.com/user-attachments/assets/d16ce255-51af-4ecb-9259-9a4d46e5281f" />

<img width="940" height="503" alt="image" src="https://github.com/user-attachments/assets/7d974304-b196-4874-adee-53d6fb380a26" />

<img width="940" height="164" alt="image" src="https://github.com/user-attachments/assets/f6ea598e-2045-47d1-8364-42586c58e187" />

<img width="940" height="329" alt="image" src="https://github.com/user-attachments/assets/9ddb5a29-a3d5-4a2b-a7b3-70c476415cd8" />

<img width="940" height="329" alt="image" src="https://github.com/user-attachments/assets/19203e8c-e01b-4749-bbcc-f9ca17f78a97" />

<img width="940" height="292" alt="image" src="https://github.com/user-attachments/assets/5f6b8af6-965a-4490-b3e5-8c5f09f650e3" />

<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/392ce4e5-4e55-4a8c-bf8a-95518810fa97" />

<img width="940" height="504" alt="image" src="https://github.com/user-attachments/assets/eb3c2702-5b37-4fe0-b5ce-921d77ebee84" />

<img width="940" height="504" alt="image" src="https://github.com/user-attachments/assets/fe61bded-51ab-48f6-97c0-910b599c7ee9" />

<img width="940" height="177" alt="image" src="https://github.com/user-attachments/assets/fed2c96c-aba4-4d7f-a29d-da62b9e12e69" />

<img width="940" height="495" alt="image" src="https://github.com/user-attachments/assets/f74946b7-5b89-4766-a077-82b2c7e6a328" />

<img width="940" height="528" alt="image" src="https://github.com/user-attachments/assets/c01f0b92-1874-4bf9-ab5a-3ca8f80bc4a9" />

<img width="940" height="504" alt="image" src="https://github.com/user-attachments/assets/fac13800-88a9-4783-be0b-8db7c5f16ede" />

<img width="940" height="474" alt="image" src="https://github.com/user-attachments/assets/9136156c-e70f-405b-82bc-fc2dc6df5e59" />

<img width="940" height="484" alt="image" src="https://github.com/user-attachments/assets/980299a7-8727-4648-a3bd-d816c5072654" />


























































