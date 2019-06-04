# Asynchronous actions:

- async: how long to run?
- poll: How frequently to check (default - 10 minutes)
 - async_status: Check status of async task


example:

```
-
  name: Deploy Web Application
  hosts: db_and_web
  tasks:
     - command: /opt/monitor.py
       asymc: 360
       pool: 0
       register: web_result
       
     - name: check status of task
       async_status: jid={{ web_result.ansible__job_id }}
       register: job_result
       until: job_result.finished
       retries: 30
     
   
