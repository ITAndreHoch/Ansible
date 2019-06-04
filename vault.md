# Ansible Vault


Ansible Vault is a feature of ansible that allows you to keep sensitive data such as passwords or keys in encrypted files,

encrypt file:

```
ansible-vault create inventory.txt
```
Using encrpyted file from pllaybook:


```

ansible-playbook playbook.yml -i inventory.txt -ask-vault-pass


```

Before start playbook ask about password

