## Turn a Linux computer as a server and access it from everywhere

### System used: 

Ubuntu 20.04


### Install Zerotier

Sign up an account on [zerotier](https://www.zerotier.com/) and create a network. It will provide us with a network ID. 

Then install the Zerotier on Linux:

```linux
curl -s https://install.zerotier.com | sudo bash
```
Output:

`......`

`*** Success! You are ZeroTier address [ eaXXXXXaXXe ].`


Start and enable the zerotier service:
```linux
sudo systemctl start zerotier-one.service
sudo systemctl enable zerotier-one.service
```
Join the network created previously using the network ID:
```linux
sudo zerotier-cli join af415e486f35688c
```
Output:

`200 join OK`

Check if we have joined the network:

```linux
sudo zerotier-cli listnetworks
```
`200 listnetworks <nwid> <name> <mac> <status> <type> <dev> <ZT assigned ips>`

`200 listnetworks af415e486f35688c Yongchang-network_001 8e:85:b7:e9:ee:f0 OK PRIVATE zt44xgwihd 10.244.46.71/16`

Extra configuration for inbound and outbound rules, `sudo` required:

```linux
iptables -I FORWARD -i ztc25p4azo -j ACCEPT
iptables -I FORWARD -o ztc25p4azo -j ACCEPT
iptables -t nat -I POSTROUTING -o ztc25p4azo -j MASQUERADE
```
### Install openssh-server:
Install ssh:
```linux
sudo apt install openssh-server
```

Check the installation process:
```linux
sudo apt list --installed | grep openssh-server
```
Output:
`WARNING: apt does not have a stable CLI interface. Use with caution in scripts.`

`openssh-server/focal-updates,now 1:8.2p1-4ubuntu0.4 amd64 [installed]`

Check ssh status:
```linux
sudo service ssh status
```
Output:
`● ssh.service - OpenBSD Secure Shell server`

`Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: e>`

`Active: active (running) since Fri 2022-04-15 17:57:43 CST; 43s ago`
     
Connect to Linux Server:

```linux
ssh username@YOUR.SERVER.IP.ADDRESS
```
> Replace your username and IP address of your Linux server.

