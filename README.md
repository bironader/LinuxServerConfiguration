# LinuxServerConfiguration
Udacity Full Stack Web Developer Nanodegree Project 7

## About
Deploy [Item-Catalog project](https://github.com/bironader/Item-Catoluge) to linux server host

## Server Information
IP address: 35.189.242.5 
SSH Port: 2200  
Username: grader  
URL site: <http://35.189.242.5/>

# Pacakges
- apache2 ---> Web Server
- libapache2-mod-wsgi -->Tool that serves Python web apps from Apache server
- postgresql ---> Relational database system
- sqlalchemy ---> SQL toolkit and ORM for Python
- Flask ---> Python web framework
- oauth2client ---> Python library for accessing resources protected by OAuth 2.0
- httplib2 ---> A comprehensive HTTP client library
- requests ----> Python HTTP Requests for Humans
- git ---> Version control tool
- facebooksdk ---> Facebook graph request

# Configuration Server:
- setup your server (Google ComuteEngine , Amazon Lightsail , etc )
- download [Putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
- open putty gen and generate private key for authentication method
- save this key 
- open private key file
- in the server add new user name it grader
`$ adduser grader`  
- give sudo privileges to grader 
`$ sudo visusdo`
- add `grader ALL=(ALL:ALL) ALL` below `root ALL=(ALL:ALL) ALL`  
- switch to grader `su grader`
- in grader home dir create .ssh dir `sudo mkdir .ssh`
- `$ cd .ssh` and create authorized_keys file `$ sudo nano authorized_keys` 
- copy private key you got from putty in authorized_key file
- ctrl+x save file
- change ssh port from 22 to 2200 `sudo nano /etc/ssh/sshd_config`
- restart ssh server `sudo service ssh restart`
- open putty desktop application 
- change port to 2200 
- in host name field `grader@yourserveripaddrees`
- now you are logged in with private key


# Firewall Configuration:
##  Allow incoming connection for SSH on port 2200, HTTP on port 80 and NTP on port 123:
  ```
  $ sudo ufw allow 2200/tcp
  $ sudo ufw allow www  
  $ sudo ufw allow ntp
  ```
  enable firewall
  `sudo ufw enable`

## Change timezone to UTC
- Configure the local timezone to UTC:  
  `$ sudo dpkg-reconfigure tzdata`
- Select UTC


## Install and configure Apache to serve a Python mod_wsgi application

1. Install Apache2 web server:  
  `$ sudo apt-get install apache2`
2. Install mod_wsgi and python-setuptools for serving Python apps from Apache:  
  `$ sudo apt-get install python-setuptools libapache2-mod-wsgi`
3. Restart Apache:  
  `$ sudo service apache2 restart`


## Install git
 -`$ sudo apt-get install git`
 - goto `cd /var/www/`
 - clone project repo `sudo git clone https://github.com/bironader/Item-Catoluge.git `
 

## Install following nessary packages

 ```
  $ sudo apt-get install python-setuptools
  $ sudo apt-get install python-psycopg2
  $ sudo pip install Flask
  $ sudo pip install oauth2client
  $ sudo pip install requests
  $ sudo pip install httplib2
  $ sudo pip install sqlalchemy
  $ sudo pip install facebook-sdk
  ```
Restart apache:  
  `$ sudo service apache2 restart`
  
# Install  PostgreSQL

- Install PostgreSQL database:   
  `$ sudo apt-get install postgresql postgresql-contrib`
  
# Deploy application

 - ` cd /var/www/Item-Catoluge` create .wsgi file `sudo nano flask.wsgi `
 - create.conf file`$ sudo nano /etc/apache2/sites-available/flask.conf`
 
 # Run application
 
 - `sudo a2ensite flask.wsgi`
 - `sudo service apache2 reload`
 -  goto  <http://35.189.242.5/>
 
## If erros occurred check logs file
-  `sudo cat /var/log/apache2/error.log`

# Third-party Resources
- [LinxServerConfiguration]https://github.com/eakmotion/LinuxServerConfiguration)
- [FlaskAppApache]http://flask.pocoo.org/docs/0.12/deploying/mod_wsgi/)
- [FireWallRule]https://cloud.google.com/compute/docs/vpc/firewalls)


  
