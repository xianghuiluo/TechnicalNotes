# Nextcloud Server Setup

- sudo snap stop/start nextcloud
- sudo nextcloud.manual-install username password
- sudo nextcloud.enable-https self-signed
- sudo ufw allow 80,443/tcp
- Edit trusted domains in */var/snap/nextcloud/current/nextcloud/config/config.php*

[Back to Contents](../README.md)
