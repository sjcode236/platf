
** run your pods only on GPU nodes with a DaemonSet**     
==To run your pods only on GPU nodes with a DaemonSet, you basically need 3 things: label/select the GPU nodes, create the namespace, then write a DaemonSet that targets those nodes. Here’s the full step-by-step for your cluster:    
▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄     
══+════════════════════════════════════════    
Your cluster layout    
- Total: 100 nodes
- GPU nodes: server23 to server36 and server63 to server72   
 
Step 1: Label your GPU nodes
=DaemonSets use nodeSelector or nodeAffinity to pick nodes. The cleanest way is to give all GPU nodes a common label.
```bash
# Label the first GPU group: server23 to server36
for i in {23..36}; do
  kubectl label nodes server${i} gpu=true --overwrite
done

# Label the second GPU group: server63 to server72  
for i in {63..72}; do
  kubectl label nodes server${i} gpu=true --overwrite
done

$kubectl get nodes -l gpu=true
=You should see 24 nodes: server23-36 + server63-72    
```
Step 2: Create a namespace    
in Bash    
kubectl create namespace gpu-agents    
```yaml
in yaml
apiVersion: v1
kind: Namespace
metadata:
  name: gpu-agents
```
kubectl apply -f namespace.yaml    






------   
weterwtrt   
