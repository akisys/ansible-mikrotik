# disclamer :
This playbook is all but done
I made this for my own home situation, feel free to make additions , improvements etc  
This playbook has been made with Routeros version 6.44.3

## how to use :

set this in your ansible cfg :  
```
[paramiko_connection]
pty=False
```

Set this in your hostvars:  
```
ansible_network_os: routeros
```

And then copy the vars (easiest way) :  
Just copy the defaults file (defaults/main.yml) to your hostvars dir and rename original main.yml (in defaults/) to something that will not be processed

Example playbook :
```

- hosts: hosts
  remote_user: admin
  connection: network_cli
  gather_facts: false
  roles:
   - ansible-mikrotik
```

## what can this playbook actually do :

### hardening
  some basic hardening stuff that mikrotik advises to do

### firewall
  add policies , not removing

### interfaces
  create a 802.3ad bond or a balance-xor bond  
  disable interfaces  
  make interface lists  

### vlans
  create vlans based on bridge filtering  
  assign interfaces to the vlan (tagged / untagged )  
  assign networks / dhcp servers to the vlan  

### wireless
  ceate a security profile (kind of basic)  
  create a virtual wlan interface  
  set the master vlan interface (and set channels and such)  

### generic:
  add a backup script and a upgrade script (not tested if the scripts actually work)  
  set ntp client

### vpn:
  still a todo

#### other remarks :
  just take a look at the default file , this maybe explain some stuff i forgot

#### todo's :

rework bond creation , to static, will need a solution like the adding of firewall policies

#### license:
MIT
