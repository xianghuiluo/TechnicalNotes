# Nextcloud Hub Setup on Ubuntu 20

## Nextcloud Install
It is very easy to install Nextcloud Hub:
```bash
sudo snap install nextcloud
```

## Administrative Account Configuration
```bash
sudo nextcloud.manual-install <username> <password>
```
## Firewall and SSL
The service is not accessible until the *http* and/or *https* ports are open:
```bash
sudo ufw allow 80,443/tcp
```
- sudo nextcloud.enable-https self-signed

## Trusted Domains
By default, the service only responds to requests made to the “localhost” hostname. We want to be able to access Nextcloud through the server’s domain name or IP address, so we’ll need to adjust this setting to accept these type of requests. The setting of trusted domains is in the configuration file: */var/snap/nextcloud/current/nextcloud/config/config.php*. So simply open the file and add more items to the 'trusted_domains'.

## Finish
Now the setup is finished, Nextcloud service can be visited with server’s domain name or IP address in your web browser: https://example.com. The Nextcloud service can be stopped and started with:
```bash
sudo snap stop/start nextcloud
```

## References
[How To Install and Configure Nextcloud on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-nextcloud-on-ubuntu-20-04)

[Back to Contents](../README.md)
