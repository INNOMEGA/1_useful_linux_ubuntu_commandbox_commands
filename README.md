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


# Set the Java to version 8 which works better than 11.06
UPDATE/CORRECTION 20200511: 11.07 seems to be OK with Lucee 5.3.6-RC

java -version

sudo apt install openjdk-8-jdk

sudo update-alternatives --config java

sudo nano /etc/environment
then add
JAVA_HOME="/usr/lib/jvm/java-8-openjdk-amd64/"

reload with 
source /etc/environment

verify
echo $JAVA_HOME

# INSTALL COMMANDBOX
curl -fsSl https://downloads.ortussolutions.com/debs/gpg | sudo apt-key add -
echo "deb http://downloads.ortussolutions.com/debs/noarch /" | sudo tee -a /etc/apt/sources.list.d/commandbox.list
sudo apt-get update && sudo apt-get install commandbox


# INSTALL CFCONFIG
go to web root directory (optional)
start Commanbox by typing
box

then install cfconfig by
install commandbox-cfconfig

# set errors to verbose
config set verboseErrors=true


# adding a datasource
Example of adding a datasource:
cfconfig datasource save name=mydatasourcename dbdriver=mysql host=db-mysql-digitaloceanlocation-yourname-someuser-somedatabasecluster.ondigitalocean.com port=25099 database=theMySQLdatabasename username=theMySQLusername password=theSuperSecretMySQLPassword

# adding a mailserver (PostmarkApp)
cfconfig mailserver save smtp=smtp.postmarkapp.com to=CommandBoxServerName username=evenmoresecret7435877453892 password=supersecret34673465

# show all cfconfig settings
config show

# start up server (and making double-sure it's using Java8, if you're into that kind of thing)
server start javaVersion=openjdk8


# commandBox does soooo much more with awesome plugins. install them. Trust Brad.
install commandbox-update-check
install commandbox-dotenv
install commandbox-bullet-train
install commandbox-hostupdater
install commandbox-service-manager@ortus   (49USD/yr/server)
install cfdocs




# CommandBox
Where is everything?
server info property=serverHomeDirectory



# CFConfig https://cfconfig.ortusbooks.com/using-the-cli/command-overview

# where are nginx things
NGINX locations:

/etc/nginx

/var/log/nginx

sudo nano /etc/nginx/nginx.conf
sudo nano /etc/nginx/commandbox.conf
sudo nano /etc/nginx/commandbox-proxy.conf
sudo nano /etc/nginx/commandbox.conf



# sample server.json file that works:

{
    "app":{
        "cfengine":"lucee@5.3.6-RC"
    },

   "JVM":{
      "javaVersion":"openjdk8"
    },
   "name":"default",
    "openbrowser":"false",
    "web":{
        "host":"127.0.1.1",
        "http":{
            "port":"8080"
        },
        "rewrites":{
            "enable":"true"
        }
    },
    "webroot":"/web"
}


# INSTALL COMMANDBOX AND LUCEE ON UBUNTU 18.04 LTS IMAGE with NGINX shortcut:

https://github.com/letskillowen/ubuntu-nginx-commandbox/
