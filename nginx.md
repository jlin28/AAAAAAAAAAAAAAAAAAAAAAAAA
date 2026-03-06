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

