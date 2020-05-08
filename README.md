# 1_useful_linux_ubuntu_commandbox_commands
I think the name says it all.

# Change Hostname on Ubuntu 18.04
 
 check hostname
 hostnamectl
 
 change hostname
 sudo hostnamectl set-hostname mynewhostname
 
 Edit hosts file
 sudo nano /etc/hosts
 
 Check if cloud.conf file exists, if yes, change that too
 ls -l /etc/cloud/cloud.cfg
 sudo nano /etc/cloud/cloud.cfg
 Search for preserve_hostname and change the value from false to true
 
 
# Nginx: 413 – Request Entity Too Large Error and Solution
Edit this file
sudo nano /etc/nginx/nginx.conf

set client body size to 2M #
client_max_body_size 2M;


# CFConfig https://cfconfig.ortusbooks.com/using-the-cli/command-overview
