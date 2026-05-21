

1. ResourceQuota Manifest (Namespace Totals)
   This file limits the total combined resources all pods can use together in the namespace.Create a file named quota.yaml:
   Create a file named quota.yaml:
```
apiVersion: v1
kind: ResourceQuota
metadata:
  name: namespace-resource-limits
  namespace: <namespace-name>
spec:
  hard:
    requests.cpu: "4"         # Total CPU requests allowed across all pods
    requests.memory: 8Gi      # Total memory requests allowed across all pods
    limits.cpu: "8"           # Total CPU limits allowed across all pods
    limits.memory: 16Gi       # Total memory limits allowed across all pods
    pods: "10"                # Maximum number of pods allowed in the namespace
```
3. dsfsdf
4. sdfdsf
5. 
   
