# Ansible
 **Installation:**
 yum install ansible
 
 
 **Configuration:**
 
 Managing servers:
 /etc/ansible/hosts
 
 Example:
 The inventory file can be in one of many formats, depending on the inventory plugins you have. For this example, the format for /etc/ansible/hosts is an INI-like (one of Ansible’s defaults) and looks like this:
```
mail.example.com

[webservers]
foo.example.com
bar.example.com

[dbservers]
one.example.com
two.example.com
three.example.com
```
The headings in brackets are group names, which are used in classifying systems and deciding what systems you are controlling at what times and for what purpose.

A YAML version would look like:
```
all:
  hosts:
    plpvmail01.proview.int:
  children:
    apphosts:
      hosts:
        plwawapp18:
    dbservers:
      hosts:
         plwawdev04:
         plwawdev05:
```

Test:

```
su - ansible
Last login: Tue Jun  4 13:47:24 CEST 2019 on pts/1
[ansible@plwawprovision ~]$ ansible apphosts -m ping
plwawapp18 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "changed": false, 
    "ping": "pong"
}

```
Hosts and non-standard ports
**badwolf.example.com:5309**

**With pattern:**
In INI:

```
[webservers]
www[01:50].example.com
```

In YAML:

```
  webservers:
    hosts:
      www[01:50].example.com:
```

For numeric patterns, leading zeros can be included or removed, as desired. Ranges are inclusive. You can also define alphabetic ranges:

```
[databases]
db-[a:f].example.com
```

**Connection type & user**

You can also select the connection type and user on a per host basis:

```
[targets]

localhost              ansible_connection=local
other1.example.com     ansible_connection=ssh        ansible_user=mpdehaan
other2.example.com     ansible_connection=ssh        ansible_user=mdehaan
```








