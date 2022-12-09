# web server
---------------------------------------------------------------------
## Here is a sample script that you can use to configure a web server:

```
#!/bin/bash

# Update the system
sudo apt-get update

# Install Apache
sudo apt-get install apache2

# Install MySQL
sudo apt-get install mysql-server

# Install PHP
sudo apt-get install php libapache2-mod-php php-mysql

# Enable the Apache mod_rewrite module
sudo a2enmod rewrite

# Backup the default Apache configuration file
sudo cp /etc/apache2/apache2.conf /etc/apache2/apache2.conf.bak

# Edit the Apache configuration file
sudo nano /etc/apache2/apache2.conf

# Add the following lines to the file (replace EXAMPLE.COM with your domain name)
<VirtualHost *:80>
    ServerName www.EXAMPLE.COM
    ServerAlias EXAMPLE.COM
    DocumentRoot /var/www/html
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

# Restart Apache
sudo service apache2 restart

# Install BIND9
sudo apt-get install bind9

# Backup the default BIND9 configuration file
sudo cp /etc/bind/named.conf.options /etc/bind/named.conf.options.bak

# Edit the BIND9 configuration file
sudo nano /etc/bind/named.conf.options

# Add the following lines to the file (replace IP_ADDRESS with the IP address of your DNS server)
forwarders {
    IP_ADDRESS;
};

dnssec-validation auto;

# Restart BIND9
sudo service bind9 restart
```

This script will install Apache, MySQL, PHP, and BIND9, as well as enable the Apache mod_rewrite module and edit the configuration files for Apache and BIND9. 
It will specify the IP address of your DNS server and enable DNSSEC validation for BIND9, and it will add a virtual host for your domain in the Apache configuration file. 
Then it will restart the Apache and BIND9 services to apply the changes.
