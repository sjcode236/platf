



**GCP Associate Cloud Engineer Google Certification -150 Demos** by Kalyan Reddy   
https://github.com/stacksimplify/google-cloud-certifications (Github repo)   
https://www.udemy.com/course/gcp-associate-cloud-engineer-google-certification  (udemy course )    

terraform-on-google-cloud  (github repo)       
https://github.com/stacksimplify/terraform-on-google-cloud/tree/main/02-Terraform-Commands     

▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄     
══+════════════════════════════════════════      
**Regions and Availbility Zones**      
a region is a specific geographical location :         
Each region represents a geographic area, like us-west1 (Oregon), europe-west3 (Frankfurt), or asia-southeast1 (Singapore).
Made of zones     
Every region contains 3 or more zones. Zones are isolated locations within a region. Example:     
Region: us-central1 (Iowa)    
Zones: us-central1-a, us-central1-b, us-central1-c     


══+════════════════════════════════════════    
**create vm instance on compute engine**    and install nginx webserver      
select project gcplearn8 -> search compute engine -> create instance    
=in Networking  -> Allow http traffic    
=enable display Device   
=create instance ; open ssh window in browser     
=upload webserver-install.sh    
 [webserver-install.sh]https://github.com/stacksimplify/google-cloud-certifications/blob/main/Compute-Engine/01-Compute-Engine-VM-Instances/01-01-VMInstance-Basics/webserver-install.sh    
=# Download directly from GitHub raw URL    
wget https://raw.githubusercontent.com/stacksimplify/google-cloud-certifications/main/Compute-Engine/01-Compute-Engine-VM-Instances/01-01-VMInstance-Basics/webserver-install.sh   
=# Or with curl   
curl -O https://raw.githubusercontent.com/stacksimplify/google-cloud-certifications/main/Compute-Engine/01-Compute-Engine-VM-Instances/01-01-VMInstance-Basics/webserver-install.sh    
  
=install nginx  package by executing webserver-install.sh  
$ curl localhost  (quering the webserver on local host )      
<!DOCTYPE html> <html> <body style='background-color:rgb(250, 210, 210);'> <h1>Welcome to StackSimplify - WebVM App1 </h1> <p><strong>VM Hostname:</strong> instance-20260703-221243</p> <p><strong>VM IP Address:</strong> 10.128.0.2 </p> <p><strong>Application Version:</strong> V1</p> <p>Google Cloud Platform - Demos</p> </body></html>      
══+════════════════════════════════════════     
01-01-VMInstance-Basics   
https://github.com/stacksimplify/google-cloud-certifications/tree/main/Compute-Engine/01-Compute-Engine-VM-Instances/01-01-VMInstance-Basics    
══+════════════════════════════════════════     
suspended state    
a suspended state means your VM is paused.      
a suspended instance preserve the OS Memoy , device state and application state; Memory state saved to disk.     
persistant disk + static IP  will be charged ; storage required for storing memory state, system state will be charged    
Reset:-   
OS forced to reboot ; Like pulling the power cord + plugging back in. No graceful shutdown      
Delete :-  
it will deleted the VM ; also the attached bootdisk for this VM     
▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄        
01-02-VMInstance-with-Startup-Script     
https://github.com/stacksimplify/google-cloud-certifications/tree/main/Compute-Engine/01-Compute-Engine-VM-Instances/01-02-VMInstance-with-Startup-Script     

▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄      
01-03-Cloud-Shell-and-gcloud-cli ; Cloud Shell and gcloud CLI     
Google cloud shell is online development and operations environment     
https://github.com/stacksimplify/google-cloud-certifications/tree/main/Compute-Engine/01-Compute-Engine-VM-Instances/01-03-Cloud-Shell-and-gcloud-cli    
=gcloud CLI commands can run in Google Cloud Shell  or client installed on laptop   

**Step-02: Create VM using gcloud CLI** ═════════════════════════════      
TAGS: Tags allow network firewall rules and routes to be applied to specified VM instances   
Important Note: Upload webserver-install.sh to Google Cloud shell if running gcloud commands on cloud shell    
[gcloud Documentation](https://docs.cloud.google.com/sdk/gcloud/reference/compute/instances)    

``` 
# Set Project
gcloud config set project PROJECT_ID
gcloud config set project gcplearn9

# Create VM Instance
gcloud compute instances create demo3-vm-gcloud \
  --zone=us-central1-a \
  --machine-type=e2-micro \
  --network-interface=subnet=default \
  --tags=http-server \
  --metadata-from-file=startup-script=webserver-install.sh 

# List Compute Instances
gcloud compute instances list   

## Optional Commands - For reference
# To list instances with their respective status and tags, run:
gcloud compute instances list --format='table(name,status,tags.list())'

# To list instances tagged with a specific tag, tag1, run:
gcloud compute instances list --filter='tags:http-server'
```
**Step-03: Stop and Start a VM Instance**  ══+════════════════════════════════════════         
```
# Stop VM Instance
gcloud compute instances stop demo3-vm-gcloud --zone=us-central1-a
gcloud compute instances list --filter='name:demo3-vm-gcloud'

# Start VM Instance
gcloud compute instances start demo3-vm-gcloud --zone=us-central1-a
gcloud compute instances list --filter='name:demo3-vm-gcloud'
```
**Step-04: Update VM using gcloud CLI**══+════════════════════════════════════════         
```
# Update VM: Enable deletion protection
gcloud compute instances update demo3-vm-gcloud \
    --zone=us-central1-a \
    --deletion-protection

# Delete VM
gcloud compute instances delete demo3-vm-gcloud --zone=us-central1-a 

## ERROR MESSAGE
ERROR: (gcloud.compute.instances.delete) Could not fetch resource:
 - Invalid resource usage: 'Resource cannot be deleted if it's protected against deletion. 

# Update VM: Disable deletion protection
gcloud compute instances update demo3-vm-gcloud \
    --zone=us-central1-a \
    --no-deletion-protection

# Delete VM
gcloud compute instances delete demo3-vm-gcloud --zone=us-central1-a
```
▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄     
01-04-VM instance with Instance Template       
https://github.com/stacksimplify/google-cloud-certifications/tree/main/Compute-Engine/01-Compute-Engine-VM-Instances/01-04-VMInstance-with-InstanceTemplate    
can create Template from scratch ; from existing template ; from existing VM instance ; 
Use CREATE SIMILAR option to create a clone of instance template ;cannot modify a template ; only clone and update to create new template   
▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄      
01-05-VM instance with Machine Images     
https://github.com/stacksimplify/google-cloud-certifications/tree/main/Compute-Engine/01-Compute-Engine-VM-Instances/01-05-VMInstance-with-MachineImages     
A machine image contains a VM’s properties, metadata, permissions, and data from all its attached disks.    
You can use a machine image to create, backup, or restore a VM.     
▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄      
01-06  Live Migration ; Create VM instance with Spot VMs     
SpotVms:- Spotvms are  Google's spare/excess compute capacity VMs; Google can terminate or preempt them with a 30-second warning whenever the capacity is needed for regular on-demand workloads. Google sells it at huge discounts.    
=no live migration or no automatic restart option for spotVMs    



















