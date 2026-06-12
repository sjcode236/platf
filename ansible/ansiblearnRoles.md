

Ansible Roles and Tasks Exaplained - Part-10    
https://www.youtube.com/watch?v=HYBFuHUQBT8    





Variables  



```
4. Understanding Variable PrecedenceAnsible provides 22 levels of variable precedence. If the same variable name is defined in multiple places, Ansible resolves the conflict using a strict hierarchy.Here is a simplified table of the most common layers used in day-to-day work, ordered from lowest importance to highest importance:Precedence OrderVariable Source LocationTypical Use Case1 (Lowest)role defaults/main.ymlDefault variables fallback for reusable roles2group_vars/all.ymlBroad environmental parameters across infrastructure3group_vars/specific_group.ymlSettings targeted to a specific tier (e.g., webservers)4host_vars/specific_host.ymlUnique overrides like explicit host IP addresses or IDs5Playbook vars blockVariables tied directly to the execution of a specific play6Task-level variables (vars inside a task)One-off overrides specific to a single execution module7Registered variables / set_factContextual indicators evaluated at runtime8 (Highest)Command line extra vars (-e)Emergency overrides and ad-hoc execution triggers



```
