Role Name
=========

A brief description of the role goes here.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook - *Work in Progress*
----------------

```
- hosts: lb
  vars:
    haproxy_package_name:           haproxy
    haproxy_frontend_port:          80
    haproxy_backend_port:           8080
    node_exporter_package_name:     node_exporter
    # packamaker/corosync vars
    pacemaker_ansible_group:        lb
    pacemaker_password:             secret
    pacemaker_ring0_addr:           ansible_all_ipv4_addresses
    pacemaker_ring0_addr_interface: 1
    pacemaker_cluster_name:         loadbalancer
    pacemaker_properties:
      stonith_enabled: "false"
    pacemaker_resources:
      - id:      virtual-ip
        type:    "ocf:heartbeat:IPaddr2"
        options:
          ip:           192.168.123.20  # this is the Virtual IP
          cidr_netmask: 24
          nic:          enp0s8
        op:
          - action:  monitor
            options:
              interval: 5s
  roles:
    - role: internal/haproxy
    - role: internal/node_exporter
    - { role: external/styopa.pacemaker, become: yes }
```

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
