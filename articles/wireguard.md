# WireGuard Setup

This note walks through the steps to set up a WireGuard server on a home computer in a home network so that a client device away from home can access the home network and also be able to direct the internet traffic through the WireGuard server.

## Home Network Environment
Here we suppose the home network consists of a home router and several devices connected to it. Let us assume the following:
- The public IP of the router is **101.92.31.37**
- The devices on the LAN of the router are assigned local IP's with DHCP
- The LAN IP range is **192.168.0.0/24**
- The WireGuard server is assigned a static LAN IP of **192.168.0.254** by the home router

## Port Forwarding and Firewall
Before we start setting up the WireGuard server and clients, port forwarding need to be set up on the home router so that a client device away from home can connect to the WireGuard server behind the home router. The default port for WireGuard is **51820/UDP**. Here we need internet traffic to 101.92.31.37/51820 be directed to 192.168.0.254/51820. Below is an example of setting the port forwarding on a home router
![Image](../data/Port-Forward.png)
To make sure incoming connections reach the server, we also need to open the port in the firewall of the server. On Ubuntu 20, simply use the following command
```bash
sudo ufw allow 51820/udp
```

## WireGuard Installation
The WireGuard tools need to be installed on both the server and the client devices. For Ubuntu 20, it can be installed simply by the following commands
```bash
sudo apt update && sudo apt install wireguard
```

## WireGuard Server
### Key Generation
The private key and the public key of the server have to be generated before we can set up server configuration file. Use the following commands to generate the private and public keys:
```bash
sudo -i
cd /etc/wireguard
umask 077
wg genkey > private.key
wg pubkey < private.key > public.key
```
Now the files *private.key* and *public.key* in the */etc/wireguard/* folder contain the private key and the public key of the server respectively.

### Server Configuration File
Create the server configuration file *home-vpn.conf* in the folder */etc/wireguard/*
```bash
touch /etc/wireguard/home-vpn.conf
```
This file will be used to create the home-vpn interface by WireGuard later. Add the following lines
```
[Interface]
Address = 192.168.1.1/24
ListenPort = 51820
```
Here we give the server an IP of 192.168.1.1 in the VPN. The */24* is a CIDR mask and means that the server will relay other traffic in the 192.168.1.1-192.168.1.254 range to peers in the VPN. It also gives us the potential to have 253 clients. Note that you can choose any set of IP's in the private IP ranges (192.168.0.0/16, 10.0.0.0/8, 172.16.0.0/12).\
Now we add the server private key to the file
```bash
echo "PrivateKey = $(cat /etc/wireguard/private.key)" >> /etc/wireguard/home-vpn.conf
```
At this point, our *home-vpn.conf* will like this
```
[Interface]
Address = 192.168.1.1/24
ListenPort = 51820
PrivateKey = YIHEAqPWDJh2DsCrsDltwtRsBuxm7lEjwF8UOEcvxkM=
```
For now let us log out of the root account by using **Ctrl+D**.

## WireGuard Client
We will create the client keys and configuration file on the server. If the client is also a device running Ubuntu 20 or a similar Linux distribution, this can also be done on the client device.
### Key Generation
First we create a folder for keeping the keys and the configuration file.
```bash
cd ~
umask 077
mkdir .wireguard && cd .wireguard
mkdir client1 && cd client1
```
Generate the keys of the client with the following commands
```bash
wg genkey > private.key
wg pubkey < private.key > public.key
wg genpsk > psk
```
The new piece here is the **Pre-Shared Key (PSK)**. The PSK is optional, but adds significant security and is very easy to add.

### Client Configuration File
Now create the client configuration file *home-vpn.conf* in the folder *~/.wireguard/client1/* and add the following two lines
```
[Interface]
Address = 192.168.1.2/32
```
We assigned the IP *192.168.1.2* to the client in the VPN. Add the client private key:
```bash
echo "PrivateKey = $(cat ~/.wireguard/client1/private.key)" >> ~/.wireguard/client1/home-vpn.conf
```
Now add the server connect details:
```bash
echo "[Peer]" >> ~/.wireguard/client1/home-vpn.conf
echo "Endpoint = 101.92.31.37:51820" >> ~/.wireguard/client1/home-vpn.conf
echo "AllowedIPs = 192.168.1.0/24" >> ~/.wireguard/client1/home-vpn.conf
echo "PublicKey = $(sudo cat /etc/wireguard/public.key)" >> ~/.wireguard/client1/home-vpn.conf
echo "PresharedKey = $(cat ~/.wireguard/client1/psk)" >> ~/.wireguard/client1/home-vpn.conf
```

[Back to Contents](../README.md)
