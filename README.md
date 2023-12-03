# Ansible role to install elasticsearch, kibana, filebeat, auditbeat, packetbeat and suricata in a cluster.

## How to use this role
The hosts inventories may look like following
```
[lxds]
elasticsearch
kibana

[nids]
sys-dev1
sys-prod1
```
## Defaults
You can changes the defaults values of defaults/main.yml file according to.

## Example Playbook
You can add this role to elasticsearch, kibana and network/host intrusion detection systems(nids) by following

```
cat elasticsiem.yml

---
- hosts: elasticsiem
  become: yes
  gather_facts: true

  roles:
    - ansible-elasticsiem


- hosts: kibana
  become: yes
  gather_facts: true

  roles:
    - ansible-elasticsiem

- hosts: nids
  become: yes
  gather_facts: true

  roles:
    - ansible-elasticsiem
```

## Example requirements.yml file
```
❯ cat requirements.yml
- src: https://github.com/masumndc1/ansible-elasticsiem.git
  scm: git
  path: roles
  version: master
```

## Run following
```
ansible-galaxy role install -f -r requirements.yml -p role
ansible-playbook -i inventories/hosts elasticsiem.yml
```
## Images
![host_events](/images/event.png)
![suricata_events](/images/suricata.png)

## License
BSD
