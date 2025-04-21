### 🚀 Ansible AWS EC2 Automation

This Ansible setup is used to manage EC2 instances on AWS — creating, starting, and stopping instances using Ansible modules and AWS credentials secured with Ansible Vault.

---

### 📋 Prerequisites

Make sure the following are installed:

- **Python** (>= 3.6)
- **pip**
- **boto3**  
  ```bash
  pip install boto3
  ```
- **Ansible** (>= 2.10)
- **Amazon AWS Ansible Collection**  
  ```bash
  ansible-galaxy collection install amazon.aws
  ```

---

### 🔐 Vault Setup

Your AWS credentials (`access_key`, `secret_key`) should be stored securely using Ansible Vault.

To edit or create encrypted vars:
```bash
ansible-vault edit group_vars/all/vault.yml --vault-password-file vault.pass
```

Example structure inside `vault.yml`:
```yaml
access_key: YOUR_AWS_ACCESS_KEY
secret_key: YOUR_AWS_SECRET_KEY
```

---

### 📦 Files Overview

- `instance_creation.yml`: Launches new EC2 instances
- `instance_start.yml`: Starts existing EC2 instances
- `instance_stop.yml`: Stops running EC2 instances
- `inventory_file`: Your Ansible inventory (can be localhost)
- `vault.pass`: File containing the vault password

---

### 🚀 Run Commands

#### Create Instances
```bash
ansible-playbook instance_creation.yml --vault-password-file vault.pass
```

#### Start Instances
```bash
ansible-playbook instance_start.yml --vault-password-file vault.pass
```

#### Stop Instances
```bash
ansible-playbook instance_stop.yml --vault-password-file vault.pass
```

📌 **Hint**: You can use the `when` clause in `instance_stop.yml` to conditionally stop specific instances based on name or tags.  
_Example use case_: Stop only instances where `name == "instance-2"`.

---
## 🔧 Notes

- Ensure the `vault.pass` file is added to `.gitignore`.
- Your PEM key file path should be accessible in WSL (check with `/mnt/c/...`)

---
