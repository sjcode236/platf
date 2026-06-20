


control plane (master )   
control plane run on multple nodes in multiple datacenters   
control pane manage the state of cluster ;  responsible for exposing the API, managing overall state,        
it  acts as the central nervous system or "brain" of a cluster, responsible for exposing the API, managing overall state, and continuously making global decisions to ensure the system matches your desired configuration. It acts as an orchestration layer that automates the scheduling, scaling, healing, and lifecycle management of your containerized applications across worker nodes.   


kube-apiserver: Acts as the main front door and communication hub for the cluster. It handles all external and internal RESTful HTTP requests, handles authentication, and acts as the sole component allowed to talk directly with the datastore.    
etcd: Serves as a highly available, consistent key-value datastore. It stores the absolute truth regarding the cluster's entire state and configuration.     
kube-scheduler: Watches for newly created Pods that do not have an assigned node yet. It evaluates resource requirements, hardware constraints, and policies to select the most suitable worker node to run those Pods.     
kube-controller-manager: Runs the core background control loops (controllers) that continuously regulate the cluster state. It detects changes (such as a node failing) and triggers the self-healing mechanisms to spin up missing pieces    





