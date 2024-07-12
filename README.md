# ansible-damengroep

# sw1


---
- name: Configure Cisco Catalyst 3750 Switch
  hosts: all
  gather_facts: no
  tasks:
    - name: Set hostname
      cisco.ios.ios_config:
        lines:
          - hostname sw-kelder-main-stack

    - name: Configure domain name
      cisco.ios.ios_config:
        lines:
          - ip domain-name zuidpoort.nl

    - name: Configure VLAN 1 with IP address
      cisco.ios.ios_config:
        lines:
          - interface Vlan1
          - ip address 172.18.1.110 255.255.255.0
          - no shutdown

    - name: Save configuration
      cisco.ios.ios_config:
        save_when: modified
