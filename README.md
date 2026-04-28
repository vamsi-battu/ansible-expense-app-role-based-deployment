# Role-Based Deployment of Expense Application using Ansible

##  Project Overview
This project demonstrates automated deployment of a multi-tier Expense application using Ansible with a role-based architecture.

The implementation follows Infrastructure as Code (IaC) principles and industry best practices by organizing automation logic into reusable roles for better scalability, maintainability, and modularity.

Each application component (frontend, backend, database) is managed using dedicated Ansible roles.

---

##  Objectives

- Automate end-to-end application deployment
- Implement role-based Ansible architecture
- Ensure reusable and modular automation
- Maintain consistency across multiple environments
- Simulate real-world DevOps workflows

---

##  Tech Stack

- Configuration Management: Ansible
- Language: YAML
- Application: Expense Application
- Infrastructure: Linux Servers (AWS EC2 / VM)
- Connectivity: SSH (Agentless)
- Version Control: Git

---

##  Architecture

- Control Node: Executes Ansible playbooks
- Managed Nodes:
  - Frontend Server (Nginx)
  - Backend Server (Node.js)
  - Database Server (MySQL)
- Roles:
  - frontend role
  - backend role
  - database role

Ansible roles encapsulate reusable configurations, enabling modular and scalable automation.

---

##  Repository Structure
├── inventory
├── roles/
│ ├── frontend/
│ ├── backend/
│ ├── database/
├── playbooks/
│ └── main.yml
├── ansible.cfg
└── README.md


---

##  Deployment Workflow

### 1. Inventory Configuration
- Define target servers
- Group servers by roles (frontend, backend, database)

### 2. Role Execution
- Each role performs specific tasks:
  - frontend → installs and configures Nginx
  - backend → deploys application and runtime
  - database → installs and configures MySQL

### 3. Playbook Execution
- Main playbook calls all roles sequentially
- Ensures proper dependency handling

---

##  Key Features

- Role-based architecture for modular automation
- Idempotent playbook execution
- Agentless configuration using SSH
- Reusable roles for scalability
- Separation of concerns across application layers

---

##  Engineering Highlights

### Modularity
Roles encapsulate specific configurations, making automation reusable and maintainable.

### Scalability
New components can be added easily by introducing new roles.

### Reliability
Idempotent execution ensures consistent system state across multiple runs.

### Maintainability
Clear separation between frontend, backend, and database logic.

---

##  Execution Steps

### Install Ansible
```bash
sudo apt update
sudo apt install ansible -y

Configure Inventory
nano inventory

Test Connectivity
ansible all -m ping -i inventory

Run Playbook
ansible-playbook -i inventory playbooks/main.yml


Application Flow
User accesses frontend (Nginx)
Frontend routes requests to backend
Backend processes application logic
Backend communicates with database
Response is returned to user

Challenges & Solutions
Challenge	Solution
Managing multi-tier dependencies	Structured execution via roles
Code duplication	Modularized into reusable roles
Debugging issues	Used Ansible verbose logging
Scalability	Implemented role-based architecture

Future Enhancements
Integrate with CI/CD pipeline (Jenkins)
Use Terraform for infrastructure provisioning
Implement dynamic inventory (AWS EC2)
Add monitoring and logging automation
Introduce Ansible Galaxy role publishing

Key Learnings
Role-based design improves scalability and maintainability
Ansible simplifies complex deployments using automation
Infrastructure as Code ensures consistency
Modular architecture aligns with real-world DevOps practices
