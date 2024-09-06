# Ansible CI/CD Pipeline Automation

## Description
This project automates the setup of a CI/CD pipeline for deploying applications to web servers using Jenkins and Ansible. It supports rolling updates and version rollbacks in case of failed deployments.

## Project Structure

/ansible-ci-cd-pipeline
│
├── Jenkinsfile                 # Jenkins pipeline configuration
├── ansible.cfg                 # Ansible configuration file
├── playbooks/
│   ├── deploy.yml              # Ansible playbook for deployment
│   ├── rollback.yml            # Ansible playbook for version rollback
│   └── update.yml              # Ansible playbook for rolling updates
├── inventory/
│   ├── production              # Inventory file for production servers
│   └── staging                 # Inventory file for staging servers
├── roles/
│   ├── setup/
│   │   ├── tasks/
│   │   │   └── main.yml        # Tasks to set up the environment
│   │   ├── handlers/
│   │   │   └── main.yml        # Handlers to restart services after deployment
│   │   ├── templates/
│   │   │   └── nginx.conf.j2   # Template for Nginx configuration
│   │   └── vars/
│   │       └── main.yml        # Variables for environment setup
│   ├── deploy/
│   │   ├── tasks/
│   │   │   └── main.yml        # Tasks for application deployment
│   │   └── vars/
│   │       └── main.yml        # Variables related to deployment
│   └── rollback/
│       ├── tasks/
│       │   └── main.yml        # Tasks for version rollback
│       └── vars/
│           └── main.yml        # Variables related to rollback
├── vars/
│   └── global.yml              # Global variables used across playbooks
├── README.md                   # Project documentation
├── LICENSE                     # License information
└── .gitignore                  # Ignore unnecessary files


## Key Features
- Automates application deployment across multiple environments.
- Supports rolling updates and version rollbacks using Ansible.
- Easily configurable Jenkins pipeline with Ansible playbooks.

## Requirements
- Jenkins
- Ansible
- Git
- Web servers (e.g., Nginx)

## Setup Instructions
1. Clone this repository:  
   `git clone https://github.com/yourusername/ansible-ci-cd-pipeline.git`
   
2. Configure your inventory files (`inventory/staging`, `inventory/production`) with the necessary hosts.

3. Set up the necessary credentials for Jenkins to access the servers.

4. Run the Jenkins pipeline, and it will automatically trigger Ansible playbooks for deployment and updates.

## Playbooks
- `playbooks/deploy.yml`: Deploys the application to web servers.
- `playbooks/rollback.yml`: Rolls back the application to a previous version.
- `playbooks/update.yml`: Performs a rolling update across web servers.

## License
This project is licensed under the MIT License.
