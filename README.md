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
sudo ufw allow 123/udp<br />
sudo ufw allow out 123/udp<br />
sudo ufw allow out 53<br />

#### change port number in /etc/ssh/sshd_config and run sudo /etc/init.d/ssh restart

sudo ufw enable

#### change ports in configuration settings in lightsail

#### Download Python 2
sudo apt-get install python finger python-pipsqlite3

#### Download requirments for my coffee app to work
sudo pip install Flask requests oauth2client sqlalchemy

#### add grader to users + add grader to sudoers + no remote passwords
sudo adduser grader<br />
sudo nano /etc/sudoers.d/grader<br />
sudo nano /etc/ssh/sshd_config<br />

#### set to UTC timezone
sudo dpkg-reconfigure tzdata

#### Installing Apache2
sudo apt-get install apache2

#### Installing mod_wsgi
sudo apt-get install libapache2-mod-wsgi

### What I learned in this project!
Almost 90% of the time during this project I was getting a 500 Internal Error when I would try to access my website. What really helped me was using
the <br />"sudo tail -50 /var/log/apache2/error.log"<br /> to figure out what kind of errors were preventing me from deploying my website properly. Otherwise,
I couldn't figure out whether or not it was a mod_wsgi configuration error or if it was the Python code that needed adjustment (it turns out it was the latter than the former.) Here are some changes I made to my Python code so that it would deploy without errors:

1.) I had to make sure to use the complete path to my client_secrets.json file as well my database files.<br />
2.) I had to change the Authorized Javascript Origins to allow my URL in my Google Developers Console so that users could log into my site with their
Google accounts.<br />

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

### Setting timezone to UTC
https://askubuntu.com/questions/138423/how-do-i-change-my-timezone-to-utc-gmt

### Other useful links
https://stackoverflow.com/questions/21124869/how-to-view-html-file-in-remote-unix-server
https://stackoverflow.com/questions/7943751/what-is-the-python-3-equivalent-of-python-m-simplehttpserver
https://stackoverflow.com/questions/7670289/sqlite3-operationalerror-unable-to-open-database-file
