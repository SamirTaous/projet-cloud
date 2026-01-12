# Project Report: Cloud Computing Infrastructure and Automation

## Student Information

| Field | Detail |
| :--- | :--- |
| **Name** | Samir Taous |
| **Supervised by** | Pr. Chaker Amrani |
| **Institution** | Université Abdelmalek Essaadi (UAE) |

---

## Project Overview

This project is a comprehensive demonstration of implementing and simulating a multi-tier cloud infrastructure, focusing on the infrastructure requirements of the Université Abdelmalek Essaadi (UAE). It transitions through theoretical simulation, manual cloud deployment, and advanced automation, effectively bridging the gap between theoretical cloud models and modern DevOps practices.

The project is structured into three distinct phases:

1.  **Infrastructure Simulation (CloudSim):** Numerical viability testing of hardware resources.
2.  **Cloud Middleware Management (OpenStack):** Manual deployment and management of a full-fledged cloud environment.
3.  **Automation and Orchestration (Terraform & Ansible):** Implementation of Infrastructure as Code (IaC) for automated, repeatable deployments.

---

## Phase I: Infrastructure Simulation (CloudSim)

The initial phase utilizes the **CloudSim** framework to numerically model and simulate the performance of the UAE University's planned cloud infrastructure. This approach allows for detailed resource planning and viability testing without incurring physical hardware costs.

### Key Simulation Components and Configuration

| Component | Description | Configuration Detail |
| :--- | :--- | :--- |
| **Datacenter** | Physical server environment simulation. | "UAE Datacenter" with 16GB of total RAM. |
| **VM (Moodle)** | Virtual machine dedicated to the E-learning platform. | 4GB RAM, 2 CPUs. |
| **VM (Scolarité)**| Virtual machine for student inscription/records service. | 2GB RAM, 1 CPU. |
| **Workload** | Simulated user activity and demand. | 10 Cloudlets simulating the load of **120,000 students**, alternating between Moodle and Scolarité services. |

---

## Phase II: Cloud Middleware Management (OpenStack)

This phase moves from simulation to hands-on deployment using **OpenStack (DevStack)** as the cloud middleware. The objective is to establish and manage a functional cloud environment, demonstrating both IaaS and basic SaaS delivery.

### Implementation Details

#### 1. Service Orchestration
The environment was set up to manage core OpenStack services essential for cloud operations:
*   **Nova:** Compute service for VM provisioning.
*   **Neutron:** Networking service for managing virtual networks and security groups.
*   **Keystone:** Identity service for user authentication and authorization.
*   **Glance:** Image service for VM template storage.

#### 2. Infrastructure-as-a-Service (IaaS) Implementation
*   **Instance:** Deployment of a minimal **CirrOS-based instance** named *"instance-iaas-cirros"*.
*   **Security:** Configuration of firewall rules (Security Groups) to allow essential network access:
    *   **ICMP (Ping):** For basic connectivity testing.
    *   **SSH (Port 22):** For remote administrative access.

#### 3. Software-as-a-Service (SaaS) Deployment
A proof-of-concept SaaS was deployed to showcase application hosting:
*   **Image Preparation:** Uploading a **CentOS-SaaS** image to the Glance registry.
*   **VM Launch:** Creation of a CentOS VM with **2GB RAM** and **10GB Disk** to host a web server.
*   **Application Hosting:** Installation and configuration of the `httpd` web server.
*   **Access:** Creation of a **Floating IP** and publishing the service via the web, hosting a demonstration page titled *"Samir's Cloud SaaS Demo"*.

---

## Phase III: Automation and Orchestration (Terraform & Ansible)

The final phase introduces **Infrastructure as Code (IaC)** principles to automate the deployment process, ensuring speed, repeatability, and consistency.

### Automation Workflow Details

| Tool | Role | Implementation |
| :--- | :--- | :--- |
| **Terraform** (v1.50.0) | **Infrastructure Provisioning** | Used to declare the desired state of the OpenStack infrastructure, including: <ul><li>Creation of an **Ubuntu instance** (*"ubuntu-nginx-terraform"*).</li><li>Definition of the required virtual **networking** components.</li><li>Allocation and association of **floating IP** addresses.</li></ul> |
| **Ansible** | **Configuration Management** | Targets the IP addresses provisioned by Terraform to perform post-deployment configuration tasks, such as: <ul><li>Automated **software installation** (e.g., Nginx web server).</li><li>Executing system-level **updates** and patches.</li><li>Ensuring the correct application state on the deployed VMs.</li></ul> |

This workflow establishes a fully automated pipeline, from cloud resource creation (Terraform) to application-level setup (Ansible).

---

## Technical Environment

| Category | Tools & Technologies |
| :--- | :--- |
| **Simulation** | Java, CloudSim |
| **Cloud Platform** | OpenStack (DevStack) |
| **OS Images** | CirrOS, CentOS 7, Ubuntu Jammy |
| **Automation** | Terraform v1.50.0, Ansible |
| **Access & Utility** | Putty (SSH Client), PuttyGen (Key Conversion) |