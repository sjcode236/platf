▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀   
══════════════════════════════════════════   


check_mounts.yml in VS Code and paste the following code:    
```
---
- name: Check mounted filesystems on MacBook
  hosts: localhost
  connection: local
  gather_facts: false

  tasks:
    - name: Run df command to see mounted filesystems
      ansible.builtin.command: df -h
      register: df_output

    - name: Display the mounted filesystems
      ansible.builtin.debug:
        msg: "{{ df_output.stdout_lines }}"
```
```
ansible-playbook check_mounts.yml
```
══════════════════════════════════════════    
Find ip address if hosts   
```
---
- name: Find Localhost IP Address
  hosts: localhost
  gather_facts: true
  tasks:
    - name: Display the default IPv4 address
      ansible.builtin.debug:
        msg: "The localhost IP address is {{ ansible_default_ipv4.address }}"

    - name: Display all IPv4 addresses (if multiple interfaces exist)
      ansible.builtin.debug:
        msg: "All available IPs: {{ ansible_all_ipv4_addresses }}"

```
══════════════════════════════════════════      







