# What is Ansible?
Ansible is an open source IT automation engine that automates provisioning, configuration management, application deployment, orchestration, and many other IT processes. 

# Features
Agentless Architecture
Declarative Language
Idempotency
Extensible Modules
Inventory Management
Simple and Secure

# Use Cases
Configuration Management: Automating system configuration, like installing software packages, setting up network services, etc.
Application Deployment: Deploying applications to multiple servers consistently and seamlessly.
Orchestration: Coordinating the deployment of multi-tier applications, ensuring that components are configured in the right sequence.
Provisioning: Automating the creation and setup of new servers, especially in cloud environments.
Continuous Delivery: Integrating Ansible into a CI/CD pipeline to automate the deployment and configuration of services.

# Basic Components
Playbooks: YAML files that define a sequence of tasks to execute on one or more nodes.
Modules: Reusable scripts that perform tasks like installing software, copying files, or configuring network devices.
Roles: A structured way of organizing playbooks, tasks, templates, and variables into reusable units for better modularity.
Inventory: A list of servers or hosts that Ansible will manage. Inventory can be static (simple text file) or dynamic (e.g., integration with cloud providers).
Controller Node: The machine where Ansible is installed. This machine sends commands to the target hosts.
Managed Nodes: These are the systems being managed by Ansible, such as Linux, Windows, or network devices.
