
scrap for asnible codes   



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
