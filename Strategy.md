**How to start playbook only on the first 2 servers:**


```
Inventory:
```
[app_servers]
app_server1
app_server2
app_server3
app_server4
app_server5
app_server6
app_server7
app_server8
app_server9
app_server10
```

Playbook.yaml:

**serial: 2**
```
-
  name: Deploy a web application
  hosts: app_servers
  serial: 2
  vars:
    db_name: employee_db
    db_user: db_user
    db_password: Passw0rd
  tasks:
  [..]
  ```
