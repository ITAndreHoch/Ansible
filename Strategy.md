

# Rolling Update Batch Size
By default, Ansible will try to manage all of the machines referenced in a play in parallel. For a rolling update use case, you can define how many hosts Ansible should manage at a single time by using the **serial** keyword:


Example: 

```
- name: test play
  hosts: webservers
  serial: 2
  gather_facts: False
  tasks:
  - name: task one
    command: hostname
  - name: task two
    command: hostname
 ```
   
In the above example, if we had 4 hosts in the group ‘webservers’, 2 would complete the play completely before moving on to the next 2 hosts:
```
PLAY [webservers] ****************************************

TASK [task one] ******************************************
changed: [web2]
changed: [web1]

TASK [task two] ******************************************
changed: [web1]
changed: [web2]

PLAY [webservers] ****************************************

TASK [task one] ******************************************
changed: [web3]
changed: [web4]

TASK [task two] ******************************************
changed: [web3]
changed: [web4]

PLAY RECAP ***********************************************
web1      : ok=2    changed=2    unreachable=0    failed=0
web2      : ok=2    changed=2    unreachable=0    failed=0
web3      : ok=2    changed=2    unreachable=0    failed=0
web4      : ok=2    changed=2    unreachable=0    failed=0
```



**How to start playbook only on the first 2 servers, next ont 3 and next on 5**


```-
  name: Deploy a web application
  hosts: app_servers
  serial:
    - 2
    - 3
    - 5
```
 
 It is also possible to list multiple batch sizes as percentages:
```
- name: test play
  hosts: webservers
  serial:
  - "10%"
  - "20%"
  - "100%"
```
You can also mix and match the values:
```
- name: test play
  hosts: webservers
  serial:
  - 1
  - 5
  - "20%"
  ```
    
 
    
