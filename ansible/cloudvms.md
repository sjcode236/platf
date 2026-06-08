
inventory.ini   
[gcpvms]
34.70.20.38     


=on google compute vm instances ;setup user and ssh-key     
```
open webssh ; sudo su -  (su to root )    
useradd mella    
passwd mella ; give blank or simple one   
usermod -aG wheel mella   (To set a user to sudo to root)    
su - username
sudo whoami
```

