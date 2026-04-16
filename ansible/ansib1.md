
▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀    
══════════════════════════════════════════    
──────────────────────────────────────────────────   
Ansible Basics    
Ansible is an open-source agentless automation tool. Unlike other configuration management systems, you don't need to install any special software on the "target" servers you want to manage. It uses SSH to connect and execute tasks.   

Core Components   
Control Node: The machine where Ansible is installed and where you run commands.; some companies has asnible runners also    
Managed Nodes: The remote servers (server1 to server10) you are controlling.    
Inventory: A file (usually hosts.ini) that lists your managed nodes.    
Modules: Small programs Ansible pushes to nodes to do work (e.g., dnf, copy, service).    
Playbooks: YAML files that describe the desired state of your systems.    

AI prompt ─────────── ───────────── ──────────────────────────   
I am trying learn ansible 
give basic tutorial of ansible   
Then give tutorial for making playbooks   
to  install  some commonly used packages in RHEL 8.9  on 10 servers say ( server1 to server10)   
then a play to check versions of  installed packages on 10 servers   
then write playbook for checking which filesystems are mounted   
then playbook to do pring test of  10 servers  
I want write these codes github repository   
then how can execute these playbooks  
──────────────────────────────────────────────────     
1. Setting Up Your Inventory
   Before writing playbooks, create a file named inventory.ini. This tells Ansible where your 10 servers are.
```
[web_servers]
server[1:10].example.com
```



