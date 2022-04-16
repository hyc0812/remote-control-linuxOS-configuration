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




yoh534@yongchang-HP:~$ curl -s https://install.zerotier.com | sudo bash
[sudo] password for yoh534: 

*** ZeroTier Service Quick Install for Unix-like Systems

*** Tested OSes / distributions:

***   MacOS (10.13+) (just installs ZeroTier One.pkg)
***   Debian Linux (7+)
***   RedHat/CentOS Linux (6+)
***   Fedora Linux (16+)
***   SuSE Linux (12+)
***   Mint Linux (18+)

*** Supported architectures vary by OS / distribution. We try to support
*** every system architecture supported by the target.

*** Please report problems to contact@zerotier.com and we will try to fix.

*** Detecting Linux Distribution

*** Found Ubuntu, creating /etc/apt/sources.list.d/zerotier.list
OK

*** Installing zerotier-one package...
Hit:1 http://dl.google.com/linux/chrome/deb stable InRelease
Ign:2 http://binaries.erlang-solutions.com/debian focal InRelease              
Hit:3 https://cli.github.com/packages focal InRelease                          
Get:4 http://download.zerotier.com/debian/focal focal InRelease [20.5 kB]      
Hit:5 https://cli.github.com/packages stable InRelease                         
Hit:6 http://ca.archive.ubuntu.com/ubuntu focal InRelease                      
Hit:7 http://packages.microsoft.com/repos/code stable InRelease                
Hit:8 http://binaries.erlang-solutions.com/debian focal Release                
Get:9 https://dl.yarnpkg.com/debian stable InRelease [17.1 kB]                 
Hit:10 https://download.docker.com/linux/ubuntu focal InRelease                
Get:11 http://ca.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]    
Hit:12 http://ppa.launchpad.net/ethereum/ethereum/ubuntu focal InRelease       
Get:13 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]     
Ign:14 http://ppa.launchpad.net/paulo-miguel-dias/pkppa/ubuntu focal InRelease 
Get:15 http://download.zerotier.com/debian/focal focal/main i386 Packages [1,140 B]
Get:16 http://ca.archive.ubuntu.com/ubuntu focal-backports InRelease [108 kB]  
Get:17 http://download.zerotier.com/debian/focal focal/main amd64 Packages [1,151 B]
Err:18 http://ppa.launchpad.net/paulo-miguel-dias/pkppa/ubuntu focal Release   
  404  Not Found [IP: 2001:67c:1560:8008::19 80]
Err:9 https://dl.yarnpkg.com/debian stable InRelease      
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 23E7166788B63E1E
Get:20 http://ca.archive.ubuntu.com/ubuntu focal-updates/main amd64 DEP-11 Metadata [278 kB]
Get:21 http://ca.archive.ubuntu.com/ubuntu focal-updates/universe amd64 DEP-11 Metadata [390 kB]
Get:22 http://ca.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 DEP-11 Metadata [944 B]
Get:23 http://security.ubuntu.com/ubuntu focal-security/main amd64 DEP-11 Metadata [40.8 kB]
Get:24 http://ca.archive.ubuntu.com/ubuntu focal-backports/main amd64 DEP-11 Metadata [7,984 B]
Get:25 http://ca.archive.ubuntu.com/ubuntu focal-backports/universe amd64 DEP-11 Metadata [30.8 kB]
Get:26 http://security.ubuntu.com/ubuntu focal-security/universe amd64 DEP-11 Metadata [66.3 kB]
Get:27 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Reading package lists... Done                                                
E: The repository 'http://ppa.launchpad.net/paulo-miguel-dias/pkppa/ubuntu focal Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: https://dl.yarnpkg.com/debian stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 23E7166788B63E1E
E: The repository 'https://dl.yarnpkg.com/debian stable InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  docutils-common libfwupdplugin1 libjs-jquery libjs-sphinxdoc
  libjs-underscore python-babel-localedata python3-alabaster python3-babel
  python3-docopt python3-docutils python3-feedparser python3-imagesize
  python3-jinja2 python3-numpydoc python3-ply python3-prompt-toolkit
  python3-roman python3-setproctitle python3-sigmavirus24-urltemplate
  python3-sphinx python3-wcwidth sphinx-common xonsh
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  zerotier-one
0 upgraded, 1 newly installed, 0 to remove and 36 not upgraded.
Need to get 3,117 kB of archives.
After this operation, 10.9 MB of additional disk space will be used.
Get:1 http://download.zerotier.com/debian/focal focal/main amd64 zerotier-one amd64 1.8.7 [3,117 kB]
Fetched 3,117 kB in 1s (2,828 kB/s)    
Selecting previously unselected package zerotier-one.
(Reading database ... 242682 files and directories currently installed.)
Preparing to unpack .../zerotier-one_1.8.7_amd64.deb ...
Unpacking zerotier-one (1.8.7) ...
Setting up zerotier-one (1.8.7) ...
Created symlink /etc/systemd/system/multi-user.target.wants/zerotier-one.service → /lib/systemd/system/zerotier-one.service.
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for systemd (245.4-4ubuntu3.15) ...

*** Enabling and starting ZeroTier service...
Synchronizing state of zerotier-one.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable zerotier-one

*** Waiting for identity generation...

*** Success! You are ZeroTier address [ ed8286a6ae ].

yoh534@yongchang-HP:~$ sudo systemctl start zerotier-one.service
[sudo] password for yoh534: 
Sorry, try again.
[sudo] password for yoh534: 
yoh534@yongchang-HP:~$ sudo systemctl enable zerotier-one.service
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
