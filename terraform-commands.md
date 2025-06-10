## 📘 Introduction

This file contains a curated list of essential Terraform commands used to manage infrastructure as code (IaC). Each command plays a specific role in the workflow—from initializing projects and planning changes, to applying configurations and destroying resources. Whether you're provisioning resources on AWS, Azure, or other cloud providers, these commands form the core of Terraform's operational lifecycle and are critical for deploying, maintaining, and evolving your infrastructure efficiently.

---

## 🚀 Terraform Commands

1. **`terraform init`**  
   This command is used to initialize the Terraform working directory and download the necessary provider plugins to manage the infrastructure.

2. **`terraform plan`**  
   This command displays a preview of the changes Terraform will make to your infrastructure, based on your configuration files.

3. **`terraform apply`**  
   This command is used to execute the Terraform plan and deploy the defined infrastructure.

4. **`terraform destroy`**  
   This command is used to destroy the existing infrastructure that was provisioned by Terraform, bringing the environment back to its original state.

5. **`terraform apply -var "variable_name=value"`**
This command is used to pass a variable value directly via the CLI, instead of hardcoding it in a file or entering it manually during runtime. This reduces human error and increases automation reliability.

6. **`terraform fmt`**
This command is used to automatically format your Terraform configuration files (such as main.tf, provider.tf, etc.) to follow a consistent style without causing any errors.

7. **`terraform validate`**
This command is used to check for errors in your Terraform configuration files. It validates the syntax and internal consistency, helping you catch mistakes before planning or applying changes.

8. **`terraform apply -var-file="custom-terraform.tfvar"`**
This command is used when the user has created a custom variable definitions file (e.g., custom-terraform.tfvar) instead of the default terraform.tfvars. It explicitly tells Terraform to use this file for input variables during runtime when applying the changes.

Note: Make sure there are no spaces in between 

9. **`terraform --version`**
This command is used to display the version of terraform installed on your system.

10. **`terraform workspace show`**
This command is used to displays the current workspace in the terraform environment

11. **`terraform workspace new <workspace-name>`**
This command is used to create a new workspace in terraform environment

12. **`terraform workspace select <workspace-name>`**
This command is used to switch workspaces within the terraform environment
