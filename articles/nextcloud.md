# Nextcloud Hub Setup on Ubuntu 20

## Nextcloud Install
It is very easy to install Nextcloud Hub:
```bash
sudo snap install nextcloud
```

## Administrative Account Configuration
```bash
sudo nextcloud.manual-install \<username\> \<password\>
```


- sudo nextcloud.enable-https self-signed
- sudo ufw allow 80,443/tcp

## Trusted Domains
By default, the service only responds to requests made to the “localhost” hostname. We want to be able to access Nextcloud through the server’s domain name or IP address, so we’ll need to adjust this setting to accept these type of requests. The setting of trusted domains is in the configuration file: */var/snap/nextcloud/current/nextcloud/config/config.php*. So simply open the file and add more items to the 'trusted_domains'.


- sudo snap stop/start nextcloud

[Back to Contents](../README.md)
