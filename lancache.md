Install Needed Software
-------------------
Install Ubuntu 16.04
apt-get install python-software-properties unzip
add-apt-repository ppa:nginx/stable
apt-get update
apt-get upgrade
apt-get install nginx
wget https://github.com/wolrah/lancache/archive/master.zip
unzip master.zip
cd lancache-master
cp -r * /etc/nginx/
mkdir /srv/www/
mkdir /srv/www/cache

Set Hostnames
--------------
Add the following to: /etc/hosts
```
10.37.0.245 	lancache-steam
10.37.0.246 	lancache-riot
10.37.0.247 	lancache-blizzard
10.37.0.248 	lancache-hirez
10.37.0.249 	lancache-origin
10.37.0.250 	lancache-sony
```
Set IP Addresses
-------------
Add the following to: /etc/network/interfaces
```
iface eth0 inet static
address 10.37.0.245
netmask 255.255.255.0

iface eth0 inet static
address 10.37.0.246
netmask 255.255.255.0

iface eth0 inet static
address 10.37.0.247
netmask 255.255.255.0

iface eth0 inet static
address 10.37.0.248
netmask 255.255.255.0

iface eth0 inet static
address 10.37.0.249
netmask 255.255.255.0

iface eth0 inet static
address 10.37.0.250
netmask 255.255.255.0
```
Restart networking
Sudo service networking restart

How to Control nginx
--------------------
sudo service nginx start
sudo service nginx stop
sudo service nginx restart

nginx log location /var/log/nginx
Error file should tell you the issues

pfSense DNS
-----------
DNS Resolver > Custom Options
```
server:
local-zone: "steampipe.steamcontent.com" redirect
local-data: "steampipe.steamcontent.com 86400 IN A 10.37.0.245"
server:
local-zone: "cs.steampowered.com" redirect
local-data: "cs.steampowered.com 86400 IN A 10.37.0.245"
server:
local-data: "content1.steampowered.com A 10.37.0.245"
server:
local-data: "content2.steampowered.com A 10.37.0.245"
server:
local-data: "content3.steampowered.com A 10.37.0.245"
server:
local-data: "content4.steampowered.com A 10.37.0.245"
server:
local-data: "content5.steampowered.com A 10.37.0.245"
server:
local-data: "content6.steampowered.com A 10.37.0.245"
server:
local-data: "content7.steampowered.com A 10.37.0.245"
server:
local-data: "content8.steampowered.com A 10.37.0.245"
server:
local-zone: "hsar.steampowered.com.edgesuite.net" redirect
local-data: "hsar.steampowered.com.edgesuite.net 86400 IN A 10.37.0.245"
server:
local-zone: "akamai.steamstatic.com" redirect
local-data: "akamai.steamstatic.com 86400 IN A 10.37.0.245"
server:
local-data: "l3cdn.riotgames.com A 10.37.0.246"
server:
local-data: "dist.blizzard.com A 10.37.0.247"
server:
local-data: "llnw.blizzard.com A 10.37.0.247"
server:
local-data: "dist.blizzard.com.edgesuite.net A 10.37.0.247"
server:
local-data: "blizzard.vo.llnwd.net A 10.37.0.247"
server:
local-data: "akamai.cdn.ea.com A 10.37.0.249"
server:
local-data: "lvlt.cdn.ea.com A 10.37.0.249"
```
