# Setting ubuntu20 on Raspberry Pi 4B

After installing ubuntu20 on RPi, ssh is enabled by default and the default account is ubuntu/ubuntu.

## create a new user account
* sudo useradd -s /bin/bash -d /home/[username]/ -m -G sudo [username]
* sudo passwd [username]
* sudo userdel -r ubuntu

## change computer name
* /etc/hosts
* /etc/hostname

[Back to Contents](../README.md)
