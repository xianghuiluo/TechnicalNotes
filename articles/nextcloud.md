# Nextcloud Server Setup

- sudo nextcloud.manual-install <username> <password>
- sudo nextcloud.enable-https self-signed
- sudo ufw allow 80,443/tcp
- Edit trusted domains in */var/snap/nextcloud/current/nextcloud/config/config.php*
- sudo snap stop/start nextcloud

[Back to Contents](../README.md)
