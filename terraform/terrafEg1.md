
▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄   
════════════════════════════════════════════     
install terrafrom on mac      



asdfad

════hello world local file════════════════════════════════════════     
```
mkdir ./helloworld
cd  helloworld

vi main.tf  

# Configure the Local Provider
terraform {
  required_providers {
    local = {
      source  = "hashicorp/local"
      version = "~> 2.5"
    }
  }
}

# Create a local file resource
resource "local_file" "hello_world" {
  filename = "${path.module}/hello.txt"
  content  = "Hello, World! Terraform is running successfully."
}
```
