# Kindle Gate Foundation - Cause Shop Frontend

## Overview

This repository contains the source code and infrastructure for the Kindle Gate Foundation Cause Shop frontend, designed for dynamic deployment on Azure DevOps. The project utilizes a blue-green deployment strategy for enhanced availability and reduced downtime. It incorporates a combination of private and public VPCs for secure and efficient resource management, with an Internet Gateway facilitating communication. Prometheus and Grafana are used for monitoring and visualization of application metrics.

## Architecture Diagram

Please refer to the architecture diagram attached in the repository for a visual representation of the infrastructure setup.

## Features

1. **Blue-Green Deployment**: Implemented across two availability groups to ensure zero downtime and seamless updates.
2. **Internet Gateway**: Facilitates communication between VPCs and the internet.
3. **Private and Public VPCs**: Segregation of resources for enhanced security and management.
4. **Prometheus**: Monitoring metrics to track the performance and health of the application.
5. **Grafana**: Visualization tool for metrics collected by Prometheus.

## Directory Structure

```
kgf-causeshop-frontend/
├── src/                   # Source code for the frontend application
├── infrastructure/        # Infrastructure as code (IaC) scripts
│   ├── azure/             # Azure-specific resources
│   ├── terraform/         # Terraform scripts for infrastructure provisioning
│   ├── kubernetes/        # Kubernetes deployment and service files
│   └── monitoring/        # Prometheus and Grafana configurations
├── docs/                  # Documentation
│   └── architecture/      # Architecture diagrams and related documents
├── tests/                 # Test cases for the application
└── README.md              # Project overview and instructions
```

## Getting Started

### Prerequisites

- Azure DevOps account
- Terraform installed locally
- kubectl installed locally
- Azure CLI installed locally

### Deployment

1. **Clone the Repository**

   ```bash
   git clone https://github.com/your-repo/kgf-causeshop-frontend.git
   cd kgf-causeshop-frontend
   ```

2. **Provision Infrastructure**

   Navigate to the `infrastructure/terraform` directory and apply the Terraform scripts to provision the required resources.

   ```bash
   cd infrastructure/terraform
   terraform init
   terraform apply
   ```

3. **Configure Kubernetes**

   Apply the Kubernetes configurations to deploy the application.

   ```bash
   cd ../kubernetes
   kubectl apply -f deployment.yaml
   kubectl apply -f service.yaml
   ```

4. **Setup Monitoring**

   Deploy Prometheus and Grafana using the configurations provided in the `monitoring` directory.

   ```bash
   cd ../monitoring
   kubectl apply -f prometheus.yaml
   kubectl apply -f grafana.yaml
   ```

### Blue-Green Deployment

The blue-green deployment strategy is implemented to ensure minimal downtime and risk during updates. This involves deploying the new version (green) alongside the current version (blue) and switching traffic to the new version after validation.

### Networking

- **Internet Gateway**: Enables communication between the VPC and the internet.
- **VPC Configuration**: 
  - **Public VPC**: Hosts the application servers accessible from the internet.
  - **Private VPC**: Hosts the database and other internal services, not directly accessible from the internet.

## Monitoring and Visualization

- **Prometheus**: Collects and stores metrics.
- **Grafana**: Provides dashboards and visualizations for the metrics collected by Prometheus.

### Accessing Grafana

1. Forward the Grafana port to access it locally:

   ```bash
   kubectl port-forward svc/grafana 3000:3000
   ```

2. Open your browser and navigate to `http://localhost:3000` to access the Grafana dashboard.

## Contributing

We welcome contributions to improve the project. Please submit a pull request or open an issue to discuss your ideas.

## License

This project is licensed under the MIT License. See the `LICENSE` file for more details.

## Contact

For any queries or support, please contact support@kindlegatefoundation.org.

---

This README provides an overview of the Kindle Gate Foundation Cause Shop frontend project, detailing the setup, deployment, and monitoring processes. For further details, refer to the specific directories and files mentioned above.# kgf-devops-demo
devops demo
