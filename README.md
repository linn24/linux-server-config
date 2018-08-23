# Deploying an Application to Linux Server
[Item Catalog application](http://54.255.235.18.xip.io/), which manages information about sport-related items in different categories, will be deployed to a linux server.

## Configuration on AWS Light Sail
1) A new instance is created in AWS Light Sail as follow.
![new instance](/images/IP_address.jpg)
2) A custom port 2200 is opened for SSH.
![new instance](/images/Firewall.jpg)

## Packages Installed
1) `sudo apt-get update`
2) `sudo apt-get upgrade`
3) `sudo apt-get install python-pip`
4) `sudo apt-get install python-flask`
5) `sudo apt-get install apache2`
6) `sudo apt-get install libapache2-mod-wsgi`
7) `sudo apt-get install git`
8) `sudo apt-get install python-sqlalchemy`
9) `sudo apt-get install postgresql`
10) `sudo apt-get install python-psycopg2`
11) `sudo apt-get install python-oauth2client`
12) `sudo apt-get install python-requests`
13) `sudo apt install finger`

## Accessing the Linux Server
`ssh ubuntu@54.255.235.18 -i LightsailDefaultPrivateKey-ap-southeast-1.pem`

## Replacing the Default Site with Item Catalog Application in Apache
1) `sudo chown -R ubuntu /etc/apache2`
2) `sudo a2dissite 000-default.conf`
3) `sudo a2ensite itemCatalogApp.conf`
4) `sudo service apache2 reload`

## Checking Apache Error Log
`sudo tail -f /var/log/apache2/error.log`

## Accessing Postgresql
1) `sudo su - postgres`
2) `psql`

## Creating New User and Giving Sudoer Access
1) `sudo adduser grader`
2) `finger grader`
3) `sudo nano /etc/sudoers.d/grader`
4) `sudo nano /etc/ssh/sshd_config`
5) `sudo service ssh restart`

## Firewall Configuration
1) `sudo ufw default deny incoming`
2) `sudo ufw default allow outgoing`
3) `sudo ufw allow 2200/tcp`
4) `sudo ufw allow 80/tcp`
5) `sudo ufw allow 123/udp`
6) `sudo ufw enable`
7) `sudo ufw status`