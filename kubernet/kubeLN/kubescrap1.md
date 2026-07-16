
** run your pods only on GPU nodes with a DaemonSet**     
==To run your pods only on GPU nodes with a DaemonSet, you basically need 3 things: label/select the GPU nodes, create the namespace, then write a DaemonSet that targets those nodes. Here’s the full step-by-step for your cluster:    
▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄     
══+════════════════════════════════════════    
Your cluster layout    
- Total: 100 nodes
- GPU nodes: server23 to server36 and server63 to server72   
==========    
Step 1: Label your GPU nodes    
------   
weterwtrt   
