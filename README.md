# Terraform Docker Container Tutorial

This project demonstrates how to use Terraform to manage Docker containers as infrastructure. It provides a simple example of pulling an image and running a container.

## 🚀 Infrastructure Overview

The current configuration deploys the following:
- **Image**: `nginx:latest`
- **Container Name**: Defined by `container_name` variable (Default: `ExampleNginxContainer`)
- **Port Mapping**: Internal `80` $\rightarrow$ External `8080`

Once deployed, the Nginx welcome page will be accessible at `http://localhost:8080`.

## 🛠️ Prerequisites

Before you begin, ensure you have the following installed:
- [Terraform](https://developer.hashicorp.com/terraform/downloads)
- [Docker](https://docs.docker.com/get-docker/) (Ensure the Docker daemon is running)

## 🚦 Getting Started

Follow these steps to deploy the infrastructure:

1. **Initialize the project** (downloads the Docker provider):
   ```bash
   terraform init
   ```

2. **Validate the configuration**:
   ```bash
   terraform validate
   ```

3. **Preview the changes**:
   ```bash
   terraform plan
   ```

4. **Apply the configuration**:
   ```bash
   terraform apply
   ```
   *(Type `yes` when prompted to confirm)*

## ⚙️ Input Variables

This project uses Terraform variables to allow customization without modifying the core code.

| Variable | Description | Type | Default |
| --- | --- | --- | --- |
| `container_name` | The name assigned to the Docker container | `string` | `ExampleNginxContainer` |

### Overriding Variables
You can override the default container name during deployment using the `-var` flag:

```bash
terraform apply -var="container_name=my-custom-nginx"
```

## 🔍 Verification

You can verify the container is running by:
- Visiting `http://localhost:8080` in your browser.
- Running `docker ps` in your terminal.

## 🗑️ Destroying Infrastructure

When you are finished with the project or need to reset your environment, use the `terraform destroy` command.

### What does `terraform destroy` do?
It looks at the `terraform.tfstate` file to identify all resources that were created by your configuration and removes them in the correct order. In this project, it will stop and remove the Docker container.

### How to run it:
```bash
terraform destroy
```
*(Type `yes` when prompted to confirm)*

## 📚 Terraform Command Reference

| Command | Description |
| --- | --- |
| `terraform init` | Initializes the working directory |
| `terraform fmt` | Rewrites configuration files to a canonical format |
| `terraform validate` | Checks whether the configuration is syntactically valid |
| `terraform plan` | Generates an execution plan |
| `terraform apply` | Applies the changes to reach the desired state |
| `terraform show` | Inspects the current state |
| `terraform state list` | Lists all resources currently in the state file |
| `terraform destroy` | Destroys all managed infrastructure |

## 📝 Note on State
Terraform maintains a `terraform.tfstate` file to track the IDs and properties of the resources it manages. **Do not commit this file to version control**, as it may contain sensitive information.