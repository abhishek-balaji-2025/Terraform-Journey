# 🌐 Terraform Remote Backend with State Locking

> **Author**: Abhishek Balaji  
> **Purpose**: To help Terraform beginners understand why remote backends and state locking are essential in a team environment.

---

## 🧩 Problem: Local `terraform.tfstate` in Team Projects

By default, Terraform stores the infrastructure state in a local file named `terraform.tfstate`.

### Here's what happens:
- A DevOps engineer writes infrastructure code in `main.tf`.
- When they run `terraform apply`, Terraform compares:
  - **Desired state** from `main.tf`
  - **Current state** from `terraform.tfstate`
- Differences are applied → real resources created or updated → state file updated.

### ❗ Issue in Team Environments:
- Each engineer may have a **different copy** of `terraform.tfstate`.
- This causes:
  - **Inconsistent state**
  - **Overwritten infrastructure**
  - **Duplicate resources**
  - **State drift**

---

## ✅ Solution: Use a Remote Backend

Remote backends store the `terraform.tfstate` file in a **centralized location** such as:

- **AWS S3**
- **Azure Blob Storage**
- **Google Cloud Storage**

### 💡 Benefits:
- 📌 **Single source of truth**
- 👥 **Safe team collaboration**
- 🔐 **Supports locking (e.g., via DynamoDB)**
- 🕓 **Supports versioning (track changes)**

---

## 🛠️ Example: Remote Backend with AWS S3 + DynamoDB

```hcl
terraform {
  backend "s3" {
    bucket         = "my-terraform-state-bucket"
    key            = "env/dev/terraform.tfstate"
    region         = "us-west-2"
    encrypt        = true
    dynamodb_table = "terraform-lock-table"
  }
}

