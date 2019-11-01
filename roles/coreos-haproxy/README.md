Role Name
=========

This role setups up a simple HAPRoxy configuration specifically for CoreOS OCP 4.x

Requirements
------------

NA

Role Variables
--------------

See Dependencies

Dependencies
------------

This role assumes you have an inventory file similar to the following:
```
---
all:
  children:
    haproxy_node:
      hosts:
        haproxy.example.com:
          ipv4: 192.168.122.10

    bootstrap_node:
      hosts:
        bootstrap.example.com:
          ipv4: 192.168.122.15
    
    masters:
      hosts:
        master1.example.com:
          ipv4: 192.168.122.20

        master2.example.com:
          ipv4: 192.168.122.21

        master3.example.com:
          ipv4: 192.168.122.22
        
    workers:
      hosts:
        worker1.example.com:
          ipv4: 192.168.122.30

        worker2.example.com:
          ipv4: 192.168.122.31

        worker3.example.com:
          ipv4: 192.168.122.32
...
```
The number of `worker` nodes is optional but should have at least 1.  Number of `masters` should be 3.
Groupnames should be left as is.  The `ipv4` variables for each host can, of course, be changed but the
name of the variable should remain the same.


Example Playbook
----------------

    - hosts: haproxyserver
      roles:
         - { role: coreos-haproxy }

License
-------

Apache

Author Information
------------------

Chuck Douglas (cdouglas@redhat.com)
http://github.com:chuckersjp/coreos-haproxy.git
