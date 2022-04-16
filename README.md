## Turn a Linux computer as a server and access it from everywhere

System: Ubuntu 20.04

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
     
Connect to remote Linux Server:

```linux
ssh username@YOUR.REMOTE.IP.ADDRESS
```
> Replace your username and IP address of your remote Linux server.


### Zerotier installation on Linux

Sign up an account on [zerotier](https://www.zerotier.com/)and create a network. Then install the Zerotier:

```linux
curl -s https://install.zerotier.com | sudo bash
```
Output:
`......`
`*** Success! You are ZeroTier address [ eaXXXXXaXXe ].`
> Here provide you the remore server address.

Start and enable the zerotier service:
```linux
sudo systemctl start zerotier-one.service
sudo systemctl enable zerotier-one.service
```
Synchronizing state of zerotier-one.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable zerotier-one
yoh534@yongchang-HP:~$ sudo zerotier-cli join af415e486f35688c
200 join OK
yoh534@yongchang-HP:~$ sudo zerotier-cli listnetworks
200 listnetworks <nwid> <name> <mac> <status> <type> <dev> <ZT assigned ips>
200 listnetworks af415e486f35688c Yongchang-network_001 8e:85:b7:e9:ee:f0 OK PRIVATE zt44xgwihd 10.244.46.71/16
yoh534@yongchang-HP:~$ iptables -I FORWARD -i ztc25p4azo -j ACCEPT
Fatal: can't open lock file /run/xtables.lock: Permission denied
yoh534@yongchang-HP:~$ sudo su
root@yongchang-HP:/home/yoh534# iptables -I FORWARD -i ztc25p4azo -j ACCEPT
root@yongchang-HP:/home/yoh534# iptables -I FORWARD -o ztc25p4azo -j ACCEPT
root@yongchang-HP:/home/yoh534# iptables -t nat -I POSTROUTING -o ztc25p4azo -j MASQUERADE
root@yongchang-HP:/home/yoh534# 
