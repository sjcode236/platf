
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
**Step 3:** Create the DaemonSet manifest   
=This example runs a DCGM Exporter, but the same pattern works for any agent. Save as gpu-daemonset.yaml:   
```yaml
apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: gpu-agent
  namespace: gpu-agents
  labels:
    app: gpu-agent
spec:
  selector:
    matchLabels:
      app: gpu-agent
  template:
    metadata:
      labels:
        app: gpu-agent
    spec:
      nodeSelector:
        gpu: "true"   # This is the key line - only schedule on GPU nodes
      tolerations:
      - key: nvidia.com/gpu
        operator: Exists
        effect: NoSchedule   # GPU nodes are often tainted, so tolerate it
      - key: nvidia.com/gpu
        operator: Exists
        effect: NoExecute
      containers:
      - name: gpu-agent
        image: nvidia/dcgm-exporter:3.3.5-3.4.0-ubuntu22.04
        env:
        - name: DCGM_EXPORTER_KUBERNETES
          value: "true"
        ports:
        - name: metrics
          containerPort: 9400
        securityContext:
          runAsNonRoot: false
          privileged: true  # DCGM needs NVML access
        volumeMounts:
        - name: proc
          mountPath: /host/proc
          readOnly: true
        - name: sys
          mountPath: /host/sys
          readOnly: true
      volumes:
      - name: proc
        hostPath:
          path: /proc
      - name: sys
        hostPath:
          path: /sys
      hostNetwork: true
      hostPID: true   # DCGM needs to see host processes
  updateStrategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 1
```
Bash    
kubectl apply -f gpu-daemonset.yaml       
**Step 5:** Verify it’s running only on GPU nodes    
```bash
# Should show 24 pods total
kubectl get pods -n gpu-agents -o wide
# Check that all pods are on server23-36 and server63-72
kubectl get pods -n gpu-agents -o wide | grep -E 'server2[3-9]|server3[0-6]|server6[3-9]|server7[0-2]'
# Make sure no pods landed on CPU nodes like server1, server50, etc
kubectl get pods -n gpu-agents -o wide | grep -v -E 'server2[3-9]|server3[0-6]|server6[3-9]|server7[0-2]'
```









------   
weterwtrt   
