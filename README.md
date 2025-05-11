# Infrastructure as Code with Terraform on Google Cloud

This repository demonstrates how to use Terraform to manage infrastructure on Google Cloud Platform (GCP). It covers the basics of Terraform, including building, changing, and destroying infrastructure as code.

## Overview

Terraform is HashiCorp's infrastructure as code tool that lets you define resources in a human-readable configuration language called HCL (HashiCorp Configuration Language). This project shows how to:

- Build and destroy infrastructure with Terraform
- Create resource dependencies
- Provision infrastructure with basic provisioning capabilities
- Use Terraform to manage Google Cloud resources

## Prerequisites

- Google Cloud Platform account
- [Terraform](https://www.terraform.io/downloads.html) installed (version 0.12+)
- Google Cloud SDK (optional, but recommended)

## Project Structure

```
terraform-gcp-demo/
├── main.tf                 # Main Terraform configuration file
├── variables.tf            # Variable definitions (optional)
├── outputs.tf              # Output definitions (optional)
├── README.md               # Project documentation
└── .gitignore              # Git ignore file
```

## Getting Started

### 1. Clone this repository

```bash
git clone https://github.com/YOUR-USERNAME/terraform-gcp-demo.git
cd terraform-gcp-demo
```

### 2. Initialize Terraform

```bash
terraform init
```

This command initializes Terraform, downloads the Google provider, and prepares your working directory.

### 3. Plan your infrastructure changes

```bash
terraform plan
```

This creates an execution plan and shows you what changes Terraform will make to your infrastructure.

### 4. Apply your infrastructure changes

```bash
terraform apply
```

When prompted, type `yes` to confirm and apply the changes.

### 5. Destroy resources when done

```bash
terraform destroy
```

When prompted, type `yes` to confirm and destroy all resources created by Terraform.

## Resources Created

This Terraform configuration creates the following resources:

1. A custom VPC network
2. A VM instance running Debian 11
3. A static IP address
4. (Optional) A Google Cloud Storage bucket

## Key Concepts Demonstrated

### Resource Dependencies

The project demonstrates both implicit and explicit dependencies:

- **Implicit dependencies**: Terraform automatically detects when one resource references another (e.g., the VM instance referencing the VPC network)
- **Explicit dependencies**: Using `depends_on` to explicitly declare dependencies between resources

### Resource Provisioning

The project uses the `local-exec` provisioner to demonstrate how to run commands locally as part of resource creation.

## Troubleshooting

### Tainted Resources

If provisioners fail, resources may be marked as "tainted." To manually mark a resource as tainted:

```bash
terraform taint google_compute_instance.vm_instance
```

This tells Terraform to recreate the resource on the next apply.

## Best Practices

1. Use version control for your Terraform configurations
2. Use modules for reusable components
3. Store state remotely for team collaboration (e.g., using Google Cloud Storage)
4. Lock state during operations to prevent concurrent modifications
5. Use variables for customizable values

## Contributing

Feel free to fork this repository and submit pull requests to improve the examples.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
