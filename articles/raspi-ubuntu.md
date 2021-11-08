# Setting ubuntu20 on Raspberry Pi 4B

After installing ubuntu20 on RPi, ssh is enabled by default and the default account is ubuntu/ubuntu. The configuration files are in /boot/firmware/.

## create a new user account
* sudo useradd -s /bin/bash -d /home/\<username\>/ -m -G sudo \<username\>
* sudo passwd \<username\>
* sudo userdel -r ubuntu

## change computer name
* /etc/hosts
* /etc/hostname

## setup wifi
* sudo apt install network-manager
* sudo nmtui
* sudo apt install avahi-daemon

## time and timezone
* timedatectl set-ntp yes
* timedatectl list-timezones
* timedatectl set-timezone Reg/Loc

[Back to Contents](../README.md)
