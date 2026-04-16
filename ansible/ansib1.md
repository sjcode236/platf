
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
give palybook to   install  7 commonly used packages in RHEL 8.9  on 10 servers say ( server1 to server10)   
give playbook to check versions of installed 7 installed packages on 10 servers   
then write playbook for checking which filesystems are mounted   
then playbook to do pring test of  10 servers  and print the ping stauts 
I want write these codes github repository   
then how can execute these playbooks  
──────────────────────────────────────────────────     
1. Setting Up Your Inventory  
   Before writing playbooks, create a file named inventory.ini. This tells Ansible where your 10 servers are.
```
[web_servers]
server[1:10].example.com
```

Playbook 1: Install 7 Common Packages:-  
This uses the dnf module, which is standard for RHEL 8.9.  
```
---
- name: Install Essential Packages on RHEL 8.9
  hosts: my_servers
  become: yes  # Runs tasks with sudo privileges
  tasks:
    - name: Ensure 7 common packages are installed
      dnf:
        name:
          - vim
          - git
          - curl
          - wget
          - net-tools
          - bind-utils
          - htop
        state: present

```

Playbook 2: Check Versions of Installed Packages
We use package_facts module to gather information  and debug to print the specific versions to your screen.  
```
---
- name: Check Package Versions
  hosts: web_servers
  tasks:
    - name: Gather package facts
      package_facts:
        manager: auto

    - name: Display version of specific packages
      debug:
        msg: "Server {{ inventory_hostname }} has {{ item }} version {{ ansible_facts.packages[item][0].version }}"
      loop:
        - vim-enhanced
        - git
      when: item in ansible_facts.packages
```
Playbook 3: Check Mounted Filesystems:-  
This uses the ansible_facts , Ansible automatically gathers "facts" about a system when a play starts. We can just filter for the mount data. 
```
---
- name: List Mounted Filesystems
  hosts: web_servers
  tasks:
    - name: Display all current mounts
      debug:
        msg: "Device {{ item.device }} is mounted at {{ item.mount }} with type {{ item.fstype }}"
      loop: "{{ ansible_facts.mounts }}"
```
Playbook 4: Ping Test and Status:-   
The ping module in Ansible doesn't just check ICMP; it verifies that Ansible can actually log in and execute Python.    
```
---
- name: Connectivity and Status Test
  hosts: my_servers
  tasks:
    - name: Execute Ansible Ping
      ping:
      register: ping_output

    - name: Print Ping Status
      debug:
        msg: "Server {{ inventory_hostname }} connectivity status: {{ ping_output.ping }}"
```
──────────────────────────────────────────────────   
GitHub Repository Structure :-   
To keep your code organized on GitHub, use a structure like this:    
```
ansible-rhel-project/
├── inventory.ini
├── install_packages.yml
├── check_versions.yml
├── check_mounts.yml
└── ping_test.yml
```
To make this professional, organize your files into a folder (repository) like this:    
Initialize: git init ansible-rhel-management   
Add Files: Put the .yml files and inventory.ini inside.    
README: Create a README.md explaining what the project does.    
To push to GitHub:     
1. Initialize the repo: git init    
2. Add files: git add .   
3. Commit: git commit -m "Initial Ansible Playbooks"   
4. Push: git remote add origin <your-repo-url> and git push -u origin main
git add .   
git commit -m "Add RHEL 8.9 management playbooks"    
git remote add origin https://github.com/yourusername/your-repo.git   
git push -u origin main

Or clone the gitrepo  from wen to local server directory     

──────────────────────────────────────────────────    
4. How to Execute    
Once your inventory and playbooks are ready, use the ansible-playbook command from your terminal:    
```
ansible-playbook -i inventory.ini install_packages.yml
```
Common flags you will need:    
-i: Point to your inventory file. ;
-K: (Capital K) Prompts for your sudo password (needed for the become: yes tasks).  ; 
-u: Specify the SSH user if it's different from your current local user (e.g., -u admin).  ;
--check: "Dry run" mode; it shows what would change without actually changing anything.       
──────────────────────────────────────────────────       







      



