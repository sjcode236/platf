
▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄      
══════════════════════════════════════════     
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
2. LimitRange Manifest (Per-Container Defaults)   
This file sets the default rules for single containers, preventing a developer from deploying a pod without resource boundaries.
Create a file named limits.yaml:
```
apiVersion: v1
kind: LimitRange
metadata:
  name: container-resource-defaults
  namespace: <namespace-name>
spec:
  limits:
  - type: Container
    default:                  # Default limit if not specified by user
      cpu: 500m
      memory: 512Mi
    defaultRequest:           # Default request if not specified by user
      cpu: 200m
      memory: 256Mi
    max:                      # Max limit a user is allowed to set
      cpu: "2"
      memory: 2Gi
    min:                      # Min request a user is allowed to set
      cpu: 100m
      memory: 128Mi

```
Apply the Manifests     
kubectl apply -f quota.yaml    
kubectl apply -f limits.yaml    


4. asdfasdf
5. gsdfgdfsg
6. abcd
7. abdd
8. kjkdf
9. wers
10. xkkmmdf
11. ksdfk;l
12. sdfk;l
13. lk;fsdf
14. sdfdsf
15. 
   
