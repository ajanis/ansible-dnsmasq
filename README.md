Role Name
=========

Installs dnsmasq http://www.thekelleys.org.uk/dnsmasq/doc.html

Requirements
------------

None

Role Variables
--------------

````
---
# defaults file for ansible-dnsmasq
config_dnsmasq: false  #defines if DNSMASQ should be configured
dhcp_boot: 'pxelinux.0,{{ inventory_hostname }},{{ pri_bind_address }}'
dhcp_scopes:  #define dhcp scopes to be used if dhcp is enabled
  - start: 192.168.1.128
    end: 192.168.1.224
    netmask: 255.255.255.0
  - start: 192.168.2.128
    end: 192.168.2.224
    netmask: 255.255.255.0
dns_search: example.org  #define your dns search here or define globally in group_vars/all
dnsmasq_nameservers:  #define your dns servers here or define globally in group_vars/all
  - 8.8.4.4
  - 8.8.8.8
enable_dnsmasq_dhcp: false  #defines if DHCP services are provided by DNSMASQ
enable_dnsmasq_dhcp_tftp: false  #defines if DHCP and TFTP services are provided by DNSMASQ
enable_tftp: false  #defines if TFTP services are provided by DNSMASQ
ntp_servers:  #defines ntp servers for clients to poll
  - 131.107.13.100
  - 216.228.192.69
pri_bind_address: '{{ ansible_default_ipv4.address }}'
pri_bind_interface: '{{ ansible_default_ipv4.interface }}'
pri_domain_name: example.org
pri_netmask_cidr: 24  #defines netmask cidr value 255.255.255.0 == 24
pri_network: '{{ ansible_default_ipv4.network }}'
tftpboot_dir: /var/lib/tftpboot  #Define tftpboot directory
````

Dependencies
------------

None

Example Playbook
----------------

````
---
- hosts: all
  become: true
  vars:
  roles:
    - role: ansible-dnsmasq
  tasks:
````

License
-------

BSD

Author Information
------------------

Larry Smith Jr.
- @mrlesmithjr
- http://everythingshouldbevirtual.com
- mrlesmithjr [at] gmail.com
