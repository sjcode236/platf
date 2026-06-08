

- Ansible ad-hoc command to find the IPv4 address of localhost    
ansible localhost -m setup -a "filter=ansible_default_ipv4"    
- print the operating system kernel version and release information, filter the facts by the word kernel:
ansible localhost -m setup -a "filter=*kernel*" -c local



- sfkpd
- rtkd
- - jdsd
  - lsld
