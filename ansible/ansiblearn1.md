

▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄    
══+════════════════════════════════════════     
Create the python Virtual Environment  on mac  
-Step : Create the Virtual Environment   
cd ~/apps   
python3 -m venv ansible-env    
-Step : Activate the Environment    
source ansible-env/bin/activate    
-Step 4: Upgrade Pip and Install Ansible    
pip install --upgrade pip    
pip install ansible    
ansible --version
▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄      
══+════════════════════════════════════════       


Variables   
You can pass variables to an Ansible playbook in several ways, but the most common and flexible method is using the --extra-vars (or -e) flag when running ansible-playbook.     
- Inline variables override variables defined in inventory or playbooks.   

1. Pass a single variable inline    
ansible-playbook site.yml -e "env=production"   
Inside your playbook, you can reference it as:  {{ env }}
2. Pass multiple variables inline   
ansible-playbook site.yml -e "env=production version=1.2.3 debug=true"
3. Pass variables from a JSON or YAML file    
ansible-playbook site.yml -e "@vars.json"
Example vars.json:
```
{
  "env": "production",
  "version": "1.2.3"
}
```    
4. Use quotes around values with spaces    
ansible-playbook site.yml -e "message='Hello World'"     


  



4. Understanding Variable PrecedenceAnsible provides 22 levels of variable precedence. If the same variable name is defined in multiple places, Ansible resolves the conflict using a strict hierarchy.Here is a simplified table of the most common layers used in day-to-day work, ordered from lowest importance to highest importance:Precedence OrderVariable Source LocationTypical Use Case1 (Lowest)role defaults/main.ymlDefault variables fallback for reusable roles2group_vars/all.ymlBroad environmental parameters across infrastructure3group_vars/specific_group.ymlSettings targeted to a specific tier (e.g., webservers)4host_vars/specific_host.ymlUnique overrides like explicit host IP addresses or IDs5Playbook vars blockVariables tied directly to the execution of a specific play6Task-level variables (vars inside a task)One-off overrides specific to a single execution module7Registered variables / set_factContextual indicators evaluated at runtime8 (Highest)Command line extra vars (-e)Emergency overrides and ad-hoc execution triggers






  

