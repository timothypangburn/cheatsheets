# BareOS Guide

## Update Ubuntu with keys and repo
```sh
RELEASE=release/latest/
DIST=xUbuntu_$(lsb_release -sr)
URL=http://download.bareos.org/bareos/$RELEASE/$DIST 
printf "deb $URL /\n" | sudo tee  /etc/apt/sources.list.d/bareos.list 
```
### After adding the repository, import the repository GPG key:
```sh
wget -q $URL/Release.key -O- | sudo apt-key add - 
```
### Update your package list index and install Bareos with MariaDB database server.
```sh
sudo apt update
```
