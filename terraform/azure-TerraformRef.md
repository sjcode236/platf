
▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄
════════════════════════════════════════════  
Terraform on Azure with IaC DevOps SRE | Real-World 25 Demos   
https://www.udemy.com/share/10571S3@6uR08gSTgUH9K9y5F84mkoteuWY7Pdw1wFZL614oWOq3KCGzCH7duIoXwmB2gl97/   
 
Terraform 101: The Ultimate Hands-On Guide [Azure Edition]  ; Mark Tinderholt      
https://www.udemy.com/course/terraform-101-azure-edition/      



▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄     
A Simple "Hello World" Example :- To get started, you create a file named main.tf 

```
# 1. Define the Provider
terraform {
  required_providers {
    azurerm = {
      source  = "hashicorp/azurerm"
      version = "~> 3.0"
    }
  }
}

provider "azurerm" {
  features {} # Required for the AzureRM provider
}

# 2. Create a Resource Group
resource "azurerm_resource_group" "example" {
  name     = "my-first-tf-rg"
  location = "West US"
}
```
▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄     
chat gpt conversation    
https://gemini.google.com/share/55a8971201f6    
▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄     
Terraform is    **idempotent:-**    
In the context of Terraform, idempotence is the property where running the same configuration multiple times results in the same end state, regardless of the starting point, without making unnecessary change   

**immutable**     
In Terraform, immutable means that once a resource (such as a Virtual Machine, database, or server) is created, it is never modified or patched in place. If the configuration changes—such as updating a server's OS or application version—Terraform destroys the existing resource and creates a brand new one with the updated configuration.   
**encapsulation:-**  
In Terraform, encapsulation refers to the practice of grouping related infrastructure resources together and hiding their internal complexity from the rest of the configuration. This is primarily achieved through Modules.      
A module is simply a set of Terraform configuration files in a single directory. By using modules, you encapsulate your logic so that a user can deploy a complex setup (like a load balancer with auto-scaling) by calling a single block of code.    
2. The Three Pillars of Encapsulation:-    
* Variables (Inputs): These are the only "knobs" the user can turn. They allow you to pass values into the encapsulated logic without the user needing to edit the resource code directly.    
* Resources (Private Logic): The actual resource blocks (e.g., azurerm_linux_virtual_machine) stay hidden inside the module. The user doesn't need to know exactly how the VM is configured, only that it is being created.
* Outputs (Interface): These define what information is shared back to the root configuration, such as a generated IP address or a Resource ID.
3. Why Use Encapsulation?    
* Reusability ;  Simplicity ; Consistency ;  

════════════════════════════════════════════     
**cohesion:-** cohesion refers to how closely related the resources within a single module one to one another. While encapsulation is about "hiding" complexity, cohesion is about "focusing" the logic.    
A highly cohesive module does one thing and does it well (e.g., managing a Virtual Network), whereas a lowly cohesive module is a "junk drawer" of unrelated resources.  To achieve high cohesion, you should group resources based on their lifecycle and function. 
* Good Cohesion (Functional): Grouping an azurerm_linux_virtual_machine with its azurerm_network_interface and azurerm_managed_disk. These resources are functionally dependent on each other to provide a "server."
* to Improve Cohesion in Your Work :-  
-Splitting by Layer: Separate your Networking (VNet/Subnets) from your Compute (VMs/Scale Sets).   
-Splitting by Lifecycle: Keep persistent data (Databases/Storage) separate from ephemeral compute (App Services/Containers).   
-Using Composition: Instead of one giant module, create several small, highly cohesive modules and call them together in your root main.tf.   

**Declarative** Terraform is designed as a Declarative tool.    
The biggest advantage of the declarative approach is ___Idempotency___. An idempotent operation is one that has no additional effect if it is called more than once with the same input parameters.    
* Declarative (The "What"): You define the end state. You tell Terraform, "I want a total of 5 Azure VMs and a Virtual Network." You don't care how it gets there; Terraform calculates the current state, compares it to your definition, and performs the necessary actions to match it. eg:- Real world eg:- Declarative: You walk up to the counter and say, "I'd like a large latte." You have defined the end state. The barista knows the "logic" required to make that happen.  
* Imperative (The "How"): You define the steps. This is like writing a Bash or PowerShell script. You tell the system: "Step 1: Create a Resource Group. Step 2: Create a VM. Step 3: Wait 30 seconds. Step 4: Create another VM." . Realworld eg:- Imperative: You walk behind the counter and say, "Take a cup. Grind 18g of beans. Pull a shot for 28 seconds. Steam the milk to 65°C. Pour the milk into the cup."







