### SOME COOL CMDS
    * adduser [USERNAME] in root
        adds a new user and prompts password
    
    * usermod -aG sudo {USERNAME] 
        grants a user mod permissions

    * su - [USERNAME] in root 
        switches you over to a user on the droplet
        if NOT in root, put sudo behind the command to swap to another user’s box
    
    * sudo su in user
        sends you to root essentially
        God mode until you use ctrl-d to turn off god mode

    * sudo passwd [USERNAME] 
        sets a sudo password for another user

--------------------------------------------------------------------------------------------------------------------------------

### STEPS TO ALLOW SSH PERMISSIONS OF YOUR DEVICE INTO THE USER
    1) On your computer, go to your .ssh folder and get your public ssh key!!!!!!!!!!!!!!!!!!!

    2) Go into your user from root or any other host that has access to that user (ssh root@YOUR_IP_ADDRESS)

    3) Use nano ~/.ssh/authorized_keys to get a terminal text editor that creates/edits the file authorized_keys

    4) Paste in your current computer’s public key
    
    5) Now ssh in !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!1

--------------------------------------------------------------------------------------------------------------------------------

### HOW DO I GENERATE AN SSH KEY PAIR IN MY USER ??
    1) Type ssh-keygen in the terminal

    2) Press Enter/Return key (.ssh will be auto created if it doesn’t exist, no need to cd into it)
    
    3) Follow the instructions your terminal gives you 
    
    4) Now you have a ssh key pair :DDDDDDDD

--------------------------------------------------------------------------------------------------------------------------------

### SETTING UP AN UFW FIREWALL
    1) In your root, enable your firewall by typing ufw enable

    2) Allow any connections with ufw allow [APPLICATION]

    3) VIEW your existing applications with ufw app list

    4) With ufw status, you can then view the status of your firewall at anytime

--------------------------------------------------------------------------------------------------------------------------------

### DISABLING ROOT LOGIN
    1) On a user with sudo permissions, open the sshd_config file with sudo nano  /etc/ssh/sshd_config
    
    2) Look for PermitRootLogin
    
    3) There, change yes✅ to no❌!!!!!!!!!!!!!
    
    4) Now save the file and exit
    
    5) Restart the sshd daemon (the thing basically in charge of handling ssh stuff) with sudo systemctl restart ssh
    
    6) Root login is now disabled hurray!!

    7) If you ever need to get in again, repeat the steps but change NO to YES

--------------------------------------------------------------------------------------------------------------------------------

### HOW TO :: INSTALL LINUX UPDATES
    1) To see if there’s updates to current packages: sudo apt update
    
    2) Pull newest updates to current packages: sudo apt upgrade

--------------------------------------------------------------------------------------------------------------------------------

### HOW TO :: INSTALL NEW LINUX PACKAGES
    1) To install, run sudo apt install
    
    2) To uninstall, run sudo apt purge

--------------------------------------------------------------------------------------------------------------------------------

### HOW TO :: INSTALL NGINX
   1) To install, run sudo apt install
    
   2) To uninstall, run sudo apt purge

--------------------------------------------------------------------------------------------------------------------------------
