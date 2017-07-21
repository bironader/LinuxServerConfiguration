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

# Configuration Steps:
- setup your server (Google ComuteEngine , Amazon Lightsail , etc )
- download [Putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
- open putty gen and generate private key for authentication method
- save this key 
- in the server add new user name it grader
`$ adduser grader`  
- give sudo privileges to grader 
`$ sudo visusdo`
- add `grader ALL=(ALL:ALL) ALL` below `root ALL=(ALL:ALL) ALL`  
- switch to grader `su grader`
- in grader home dir create .ssh dir `sudo mkdir .ssh`
- `cd .ssh` and create authorized_keys file `sudo nano authorized_keys` 
- copy private key you got from putty in authorized_key file
- ctrl+x save file

