# 1. What is Ansible Vault?

#### Ansible Vault is a feature that lets us encrypt sensitive data like password.Only someone with the correct password can decrypt and use the data.

# 2. When would you use Ansible Vault?

### I use Ansible Vault whenever I need to store secrets — like database passwords, AWS credentials, or private keys — inside playbooks or variable files. This ensures security while still allowing automation.

# 3. How do you encrypt a file with Ansible Vault?

### ansible-vault encrypt secrets.yaml

# 4. How do you edit an encrypted file?

### ansible-vault edit secrets.yaml

# 5. How do you use an encrypted file in a playbook?

  Answer (with example):

    “I can include the encrypted file like any other vars file:

vars_files:
  - secrets.yml

Then I run the playbook with:

ansible-playbook playbook.yml --ask-vault-pass

It will prompt for the vault password.”
