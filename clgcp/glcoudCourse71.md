



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
    https://github.com/stacksimplify/google-cloud-certifications/blob/main/Compute-Engine/01-Compute-Engine-VM-Instances/01-01-VMInstance-Basics/webserver-install.sh    
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




