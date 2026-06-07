
scrap for asnible codes   




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
