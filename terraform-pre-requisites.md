# Pre-requisites

1. **Install an IDE** of your choice (e.g., Visual Studio Code, IntelliJ, etc.).
2. **Install Terraform** on your machine.
3. **Install AWS CLI** (Command Line Interface).
4. **Create an IAM user** in AWS specifically for Terraform usage.
5. **Provide security credentials** (Access Key ID and Secret Access Key) for the IAM user to use with Terraform.
6. **Store those security credentials** (Access Key ID and Secret Access Key) within an **encrypted secure vault** (e.g., Bitwarden, HashiCorp Vault).
7. **Perform AWS CLI configuration** by running `aws configure` and entering:
   - Access Key ID  
   - Secret Access Key  
   - Default AWS region (e.g., `us-east-1`)  
   - Default output format (e.g., `json`, `text`, or `table`)  
8. *(Optional)* **Set up version control** (e.g., Git) to manage your Terraform code securely and collaborate efficiently.
