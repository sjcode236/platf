
inventory.ini   
[gcpvms]   
34.70.20.38   
34.171.8.39   
35.225.152.163  


=on google compute vm instances ;setup user and ssh-key     
```
open webssh on cloud browser ;
sudo su -  (su to root )    
useradd mella    
passwd mella ; give blank or simple one   
usermod -aG wheel mella   (To set a user to sudo to root)    
su - username
sudo whoami
##enable password Authentication   
sudo vi /etc/ssh/sshd_config
PasswordAuthentication yes
sudo systemctl restart sshd
```
==setting up sshkey for passwordless login    
At macbook Terminal   
ssh-keygen -t rsa    
ssh-copy-id mella@34.70.20.38    
ssh-copy-id mella@34.171.8.39    
ssh-copy-id mella@35.225.152.163     
ssh  34.70.20.38      
▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀     
══════════════════════════════════════════    











