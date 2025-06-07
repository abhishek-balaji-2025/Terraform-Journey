| File Name            | What It Does                                                                 | Logical Understanding                                                                 |
|----------------------|------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| `main.tf`            | Defines what infrastructure to create (e.g., EC2 instances, S3 buckets).     | Like a blueprint — it tells Terraform what your setup should look like.               |
| `provider.tf`        | Specifies the cloud provider (AWS, Azure, GCP) and how to connect to it.     | Like giving Terraform a phone number and instructions to talk to the cloud.           |
| `variables.tf`       | Defines input variables to make the config dynamic.                          | Like creating blank fields that you’ll fill in later (e.g., region, instance type).   |
| `terraform.tfvars`   | Stores the actual values for input variables defined in `variables.tf`.       | Like the filled-out form you hand to Terraform before it begins.                      |
| `terraform.tfstate`  | Keeps track of the current real-world infrastructure state.                  | It’s Terraform’s memory — helps it know what it already built or changed.             |
| `terraform.lock.hcl` | Locks the provider versions used to ensure consistency.                      | A version freeze file — avoids mismatches across different computers.                 |
| `output.tf`          | Defines output values to display after `terraform apply`.                    | Like a receipt or summary — shows useful results like IPs, URLs, or ARNs.             |
