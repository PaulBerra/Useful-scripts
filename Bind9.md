## Here is a sample script that you can use to configure BIND9, which is a DNS server:

```
#!/bin/bash

# Update the system
sudo apt-get update

# Install BIND9
sudo apt-get install bind9

# Backup the default configuration file
sudo cp /etc/bind/named.conf.options /etc/bind/named.conf.options.bak

# Edit the configuration file
sudo nano /etc/bind/named.conf.options

# Add the following lines to the file (replace IP_ADDRESS with the IP address of your DNS server)
forwarders {
    IP_ADDRESS;
};

dnssec-validation auto;

# Restart BIND9
sudo service bind9 restart

```

This script will install BIND9, backup the default configuration file, and edit it to specify the IP address of your DNS server and enable DNSSEC validation.
Then it will restart the BIND9 service to apply the changes.

## commands to check the configuration :

```
named-checkconf /etc/named.conf
```

if there is no ouptput, configuration is fine
<br>
Same in chroot environment :
```
named-checkconf -t /var/named/chroot /etc/named.conf 
```
check zone file :
```
named-checkzone domain.net /var/named/domain.net.db 
```
