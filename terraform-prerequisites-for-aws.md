# Introduction to Terraform for Beginners

## 1. Provider

A **provider** is a set of plugins that allows Terraform to interact with a specific cloud service such as **AWS, Azure, GCP**, etc.  
Think of the provider as a **middleman** that enables Terraform to communicate with various cloud platforms.

> **Note:** Terraform code is written in **HashiCorp Configuration Language (HCL)**.

---

## Why Use Terraform?

- **Cloud Agnostic**: Works with many cloud providers, unlike tools like AWS CloudFormation which are vendor-specific.
- **Infrastructure as Code (IaC)**: You define and manage your infrastructure using code.
- **Version Control**: You can store your infrastructure definitions in Git and track changes over time.
- **Modular and Reusable**: Use modules to break infrastructure into reusable components.
- **Automated and Scalable**: Apply changes repeatedly and reliably across environments (dev/stage/prod).

---

## Choosing a Provider

You can explore and select providers from the **Terraform Provider Registry**:  
🔗 [Terraform Provider Registry](https://registry.terraform.io/browse/providers)

---

## Getting Started with Terraform

### Step 1: Create an IAM User

To allow Terraform to interact with AWS, you need to **create an IAM user** with appropriate permissions (e.g., **Administrator Access**).  
This IAM user is used **for authentication purposes**, so that Terraform can securely access and manage cloud resources on your behalf.

✅ **Reuse the IAM user** for multiple Terraform projects.  
No need to create a new one unless you want to **isolate access** or enforce **different policies** for different use cases.

---

### Step 2: Install AWS CLI

#### For Windows:

1. **Download the installer**:  
   https://awscli.amazonaws.com/AWSCLIV2.msi

2. **Run the MSI installer** by double-clicking the downloaded file.

3. **Verify installation**:  
   Open Command Prompt and run:

   ```bash
   aws --version

## Step 3: Install Terraform

Follow the instructions in the official documentation to install Terraform:  
🔗 [Terraform Installation Guide](https://developer.hashicorp.com/terraform/install)

---

## Step 4: Configure AWS Credentials for Terraform

Use AWS CLI to configure your credentials:

```bash
aws configure



