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

### 5. State Tracking:
- Terraform uses a file called **terraform.tfstate** to store the current state of your infrastructure.
- After applying changes, Terraform updates this file to reflect the new real-world infrastructure.
- Future runs compare **main.tf** (desired state) with **terraform.tfstate** (current state) to determine required changes.
