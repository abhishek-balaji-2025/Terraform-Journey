# Terraform-Journey
This repository documents everything I’ve learned (and continue to learn) about Terraform. From setting up providers and managing resources to creating reusable modules and using remote backends, this is my personal exploration of automating infrastructure on platforms like AWS, Azure, and more.

| File Name            | What It Does                                                                 | Logical Understanding                                                                 |
|----------------------|------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| `main.tf`            | Defines what infrastructure to create (e.g., EC2 instances, S3 buckets).     | Like a blueprint — it tells Terraform what your setup should look like.               |
| `provider.tf`        | Specifies the cloud provider (AWS, Azure, GCP) and how to connect to it.     | Like giving Terraform a phone number and instructions to talk to the cloud.           |
| `variables.tf`       | Defines input variables to make the config dynamic.                          | Like creating blank fields that you’ll fill in later (e.g., region, instance type).   |
| `terraform.tfvars`   | Stores the actual values for input variables defined in `variables.tf`.       | Like the filled-out form you hand to Terraform before it begins.                      |
| `terraform.tfstate`  | Keeps track of the current real-world infrastructure state.                  | It’s Terraform’s memory — helps it know what it already built or changed.             |
| `terraform.lock.hcl` | Locks the provider versions used to ensure consistency.                      | A version freeze file — avoids mismatches across different computers.                 |
| `output.tf`          | Defines output values to display after `terraform apply`.                    | Like a receipt or summary — shows useful results like IPs, URLs, or ARNs.             |

# Terraform Working Principle (Simplified)

### 1. Define Configuration:
- The user creates **main.tf** to define the desired infrastructure using resources like `aws_instance`, `aws_s3_bucket`, etc.
- A **provider.tf** file specifies the cloud provider (e.g., AWS) and its configuration, allowing Terraform to authenticate and communicate with it.

### 2. Initialize the Project:
- Run `terraform init` to initialize the working directory.
- This downloads the necessary provider plugins and prepares the backend.

### 3. Preview Changes:
- Run `terraform plan` to generate an execution plan.
- This shows what Terraform will create, update, or destroy to match the desired state defined in **main.tf**.

### 4. Apply Changes:
- Once satisfied with the preview, run `terraform apply`.
- Terraform makes the actual changes to your cloud infrastructure (e.g., launching EC2 instances).

### 5. Apply with Variables:
- Use `terraform apply -var "variable=variable_name"` to pass variables directly via the CLI.
- This helps automate deployments and avoids manual input errors, especially useful in CI/CD pipelines.

### 6. State Tracking:
- Terraform uses a file called **terraform.tfstate** to store the current state of your infrastructure.
- After applying changes, Terraform updates this file to reflect the new real-world infrastructure.
- Future runs compare **main.tf** (desired state) with **terraform.tfstate** (current state) to determine required changes.

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

🔐 State Locking in Terraform

State locking ensures that only one operation can modify the terraform.tfstate at a time.
When a command like terraform apply runs, Terraform locks the state file to prevent concurrent updates by other users or processes.

✅ A temporary file named terraform.tfstate.tflock is created during this process.

This prevents race conditions, corruption, and ensures safe collaboration in team environments.

For remote backends like AWS S3 + DynamoDB, Terraform uses the DynamoDB table to manage locks automatically.
