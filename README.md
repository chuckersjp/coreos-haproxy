# coreos-haproxy
This is a simple role that will generate a simple HAProxy server to server for a CoreOS OCP 4.x cluster.
Technically it can be used for anything but it focuses on settings needed for OCP 4.x

# Problem definition
You will need a load balancer properly configured for traffic to your OCP Control Plane and Worker nodes.

# Assumptions
This playbook will require an inventory file similar to the following:
```
---
all:
  children:
    bootstrap_node:
      hosts:
        bootstrap:
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

As this was designed with OCP 4.x in mind, you will need 3 masters and a bootstrap node to start with.  The number
worker nodes is optional but at least 1 is recommended (required?)

# Clean up
`IMPORTANT`
Once your OCP cluster is up and running, you will need to remove the bootstrap node from the HAProxy configuration.
That is what the `remove_bootstrap.yml` file is for.  This is NOT called as part of the normal workflow as there is
no telling how long it will take to stand up the cluster.  It is provided here as a convience in the 
`role/coreos-haproxy/tasks` directory.

