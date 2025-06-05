## HashiCorp Official Terraform Installation Guide (Debian/Ubuntu)

HashiCorp officially maintains and signs packages for the following Linux distributions:

- `Ubuntu/Debian`
- `CentOS/RHEL`
- `Fedora 40`
- `Fedora 41`
- `Amazon Linux`

---

## Step 1: Install Prerequisites

Ensure your system is up to date and install required packages:

`sudo apt-get update && sudo apt-get install -y gnupg software-properties-common`

---

## Step 2: Install the HashiCorp GPG Key

`wget -O- https://apt.releases.hashicorp.com/gpg | gpg --dearmor | sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg > /dev/null`

---

## Step 3: Verify the GPG Key Fingerprint

`gpg --no-default-keyring --keyring /usr/share/keyrings/hashicorp-archive-keyring.gpg --fingerprint`

### Expected output:

`/usr/share/keyrings/hashicorp-archive-keyring.gpg`  
`-------------------------------------------------`  
`pub   rsa4096 XXXX-XX-XX [SC]`  
`AAAA AAAA AAAA AAAA`  
`uid           [ unknown] HashiCorp Security (HashiCorp Package Signing) <security+packaging@hashicorp.com>`  
`sub   rsa4096 XXXX-XX-XX [E]`

> Tip: Refer to the official packaging guide at `https://developer.hashicorp.com/terraform/downloads`.  
> You can also verify the key on the HashiCorp security page under Linux Package Checksum Verification: `https://www.hashicorp.com/security`.

---

## Step 4: Add the HashiCorp Repository

This command uses your system’s release codename (like `jammy`, `focal`, etc.):

`echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(grep -oP '(?<=UBUNTU_CODENAME=).*' /etc/os-release || lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list`

---

## Step 5: Update Package Information

`sudo apt update`

---

## Step 6: Install Terraform

`sudo apt-get install terraform`

---

You now have the official version of `Terraform` installed and maintained via the system’s package manager.

