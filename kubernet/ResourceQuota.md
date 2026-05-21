
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


4. To test the ResourceQuota,   
you can deploy a pod that requests more resources than the namespace allows. Based on the quota.yaml configuration provided earlier (which limits total requests to 8Gi of memory), deploying a single pod that asks for 10Gi will trigger an immediate rejection from the Kubernetes API.   
a- Create a Violating Pod Manifest:- Create a file named violating-pod.yaml:   
```
apiVersion: v1
kind: Pod
metadata:
  name: oversized-test-pod
  namespace: <namespace-name>
spec:
  containers:
  - name: stress-test
    image: nginx
    resources:
      requests:
        memory: "10Gi"   # Exceeds the 8Gi namespace total request quota
        cpu: "1"
      limits:
        memory: "10Gi"
        cpu: "1"
```
b-Attempt to Apply the Manifest     
  kubectl apply -f violating-pod.yaml      
c- Expected Error Result   
The Kubernetes API server will immediately block the deployment and print an error message directly to your terminal. It will look like this:   
```
Error from server (Forbidden): error when creating "violating-pod.yaml": pods "oversized-test-pod" is forbidden: exceeded quota: namespace-resource-limits, requested: requests.memory=10Gi, used: requests.memory=0, limited: requests.memory=8Gi
```
d-Alternative Test: Exceeding Pod Count Quota     
Our quota.yaml also restricted the maximum number of pods to 10. You can test this constraint by scaling a standard deployment to 11 replicas:bash   
```
kubectl create deployment nginx-test --image=nginx -n <namespace-name>
kubectl scale deployment nginx-test --replicas=11 -n <namespace-name>
```


6. asdfasdfasdf
7. gsdfgdfsg
8. abcd
9. abdd
10. kjkdf
11. wers
12. xkkmmdf
13. ksdfk;l
14. sdfk;l
15. lk;fsdf
16. sdfdsf
17. 
   
