### INTERACTING WITH YOUR SERVER
    * systemctl status nginx
        checks if nginx is alive!
    
    * sudo systemctl stop nginx
        stops your server 👍
  
    * sudo systemctl start nginx
        starts your server back up if stopped !!!
  
    * sudo systemctl restart nginx
        does basically what stop and start does but in quick succession
  
    * sudo systemctl reload nginx
        restarts your server without cutting off any connections (for config changes!!!!!!!!!!)
      
    * sudo systemctl disable nginx
        to have nginx NOT start up as soon as your server is up
      
    * sudo systemctl enable nginx
        to have nginx start up as soon as server is up (default setting)

### GETTING GUNICORN TO RUN ON YOUR DOMAIN _LOCALLY_
    1) Run **sudo nano /etc/hosts**
    
    2) Take your VM's outward facing IP address and paste that in below the other addresses
    
    3) Next to it put [YOUR_DOMAIN] [www.YOUR_DOMAIN]
    
    4) now, if you run ping [YOUR_DOMAIN], it should ping your server's ip and if you run curl [YOUR_DOMAIN], it should 
    return the contents of your flask app!!!!!!
    
    5) This essentially maps a hostname (in this case your domain) to a server's ip and allows you to bypass the 
    need for an established DNS (domain name system) or essentially the internet's phonebook (connecting domains to ips)
    
    6) To make the changes to **/etc/hosts** permanent, make the same change in **/etc/cloud/templates/hosts.debian.tmpl**   

