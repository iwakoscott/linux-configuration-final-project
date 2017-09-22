# Linux Server Configuration Final Project - Item Catalog Deployment

Author: Satoshi Scott Iwako

## Necessary Information:
**IP Address**|**35.162.223.26**
:-----:|:-----:
SSH Port |2200
URL|http://35.162.223.26/

## Summary of Configuration

### Deny all incoming and allow all outgoing
sudo ufw default deny incoming
sudo ufw default allow outgoing

#### Set SSH to port 2200
sudo ufw allow 2200/tcp

#### Set http to port 80
sudo ufw allow www

#### Allow NTP on port 123
sudo ufw allow 123/udp
sudo ufw allow out 123/udp
sudo ufw allow out 53

#### change port number in /etc/ssh/sshd_config and run sudo /etc/init.d/ssh restart

sudo ufw enable

#### change ports in configuration settings in lightsail

#### Download Python 2
sudo apt-get install python
sudo apt-get install finger
sudo apt-get install python-pip
sudo apt-get install sqlite3

sudo pip install Flask requests oauth2client sqlalchemy

#### add grader to users
sudo adduser grader
sudo nano /etc/sudoers.d/grader # add to sudoers
sudo nano /etc/ssh/sshd_config # edit so no passwords work you need a private key

#### set to UTC timezone
sudo dpkg-reconfigure tzdata

#### Installing Apache2
sudo apt-get install apache2

#### Installing mod_wsgi
sudo apt-get install libapache2-mod-wsgi


## Useful Links

### Most useful link to set up mod_wsgi correctly
https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps


### How to configure the ports correctly?
https://askubuntu.com/questions/174981/how-do-i-configure-ufw-to-allow-ssh-on-another-port
https://unix.stackexchange.com/questions/3568/how-to-switch-between-users-on-one-terminal
https://askubuntu.com/questions/709843/how-to-configure-ufw-to-allow-ntp-to-work


### Dont allow public use of .git!
https://en.internetwache.org/dont-publicly-expose-git-or-how-we-downloaded-your-websites-sourcecode-an-analysis-of-alexas-1m-28-07-2015/
https://askubuntu.com/questions/652095/cant-find-httpd-conf

### Other useful links
https://stackoverflow.com/questions/21124869/how-to-view-html-file-in-remote-unix-server
https://stackoverflow.com/questions/7943751/what-is-the-python-3-equivalent-of-python-m-simplehttpserver
https://stackoverflow.com/questions/7670289/sqlite3-operationalerror-unable-to-open-database-file
### Setting timezone to UTC
https://askubuntu.com/questions/138423/how-do-i-change-my-timezone-to-utc-gmt
