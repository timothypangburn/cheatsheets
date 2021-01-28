## Cheat Sheet for Day to Day Commands

##### Ansible Run with Make to log and screen

unbuffer make <make tag> limit=<hostname> | tee logfile.log

##### Find the size of sub-directories 

du -k | sort -n | perl -ne 'if ( /^(\d+)\s+(.*$)/){$l=log($1+.1);$m=int($l/log(1024)); printf  ("%6.1f\t%s\t%25s  %s\n",($1/(2**(10*$m))),(("K","M","G","T","P")[$m]),"*"x (1.5*$l),$2);}'

##### Map remote host via port on ssh

ssh -L 9000:localhost:5984 username@ip`. 

##### Connect to couchDB after mapping port via ssh

localhost:9000/_utils/

##### Windows remote desktop

rdesktop -g 1280x900 -d WILDCARD -u timothy.pangburn 10.1.9.186

##### Default Server Prompt Color

PS1='${debian_chroot:+($debian_chroot)}\[\033[38;5;201m\]\u\[$(tput sgr0)\]\[\033[38;5;15m\]@\[$(tput sgr0)\]\[\033[38;5;201m\]\h\[$(tput sgr0)\]\[\033[38;5;15m\]:\[$(tput sgr0)\]\[\033[38;5;51m\]\W\[$(tput sgr0)\]\[\033[38;5;15m\]\\$ \[$(tput sgr0)\] '

##### Force a Log Rotate

sudo logrotate --force $CONFIG_FILE

##### Check Time Date Sync on Ubuntu

timedatectl

##### Check FreeNAS for Issues with Active Directory

root@freenas# grep smbd /var/log/messages

root@freenas# wbinfo -t # test connection to AD

##### Open VPN Connection

sudo openvpn --config ~/.cert/enforcercorp1-UDP4-1194-timothy.pangburn-config_201710b.ovpn

* If connection is bad check time on firewall vs current system

##### Clean out applications and Kernels that are not needed

###### <Ubuntu 14.04

sudo apt-get clean && sudo apt-get autoclean && sudo apt-get autoremove

###### >Ubuntu 16.04

sudo apt clean && sudo apt autoclean && sudo apt autoremove

###### Check for active TCP ports

netstat -plnt

##### Better

ss -{4|6} state listening

###### Add Group to user - Ubuntu

adduser <user_name> <group_name>

###### Check groups on user

Id <user_name>

###### Routes

sudo route add -net 192.168.10.108 netmask 255.255.255.255 tun0

sudo route del -net 192.168.10.108 netmask 255.255.255.255 tun0

###### better 

sudo ip route add 192.168.10.108/32 via  tun0

###### Kill off Many Processes

for pid in $(ps -ef | awk '/process_cf/ {print $2}'); do kill -9 $pid; done

###### Time since last reboot

$> uptime

00:14:57 up 11 min,  1 user,  load average: 0.02, 0.04, 0.05

$> last reboot

reboot   system boot  3.13.0-144-gener Thu Apr  5 00:03 - 00:15  (00:11)    reboot   system boot  3.13.0-144-gener Wed Apr  4 22:34 - 00:02  (01:27)    wtmp begins Wed Apr  4 22:28:25 2018

#### Set root user editor (or default) to vim/vi/emacs

**sudo** EDITOR=vim visudo

#### Set Bash Edit Mode to vi

set -o vi

#### Set tsch Edit Mode to vi

bindkey -v

#### Get simple directory layout on the CLI

**tree** -d -l 2

#### Get human readable size of directory only one level deep

**du** -sh --maxdepth=1

#### Grep results to VIM

**grep** -**l** -R "something you're searching for" ./path/**to**/search | xargs **vim**

#### List all enabled services on Server

systemctl list-unit-files | grep enabled

#### Route traffic correctly if on VPN to HQ
#### for WiFi using the 10.0.0.0/8 address space

sudo ip route add 10.1.0.0/16 via 10.249.253.225 dev tun0 

#### Passwords Change (LDAP, SAMBA, Kerbros)

* [https://web.mit.edu/kerberos/krb5-devel/doc/user/user_commands/kpasswd.html](https://web.mit.edu/kerberos/krb5-devel/doc/user/user_commands/kpasswd.html)

* web.mit.edu

* **[kpasswd — MIT Kerberos Documentatio**n](https://web.mit.edu/kerberos/krb5-devel/doc/user/user_commands/kpasswd.html)

* [https://web.mit.edu/kerberos/krb5-1.5/krb5-1.5.4/doc/krb5-admin/Changing-Passwords.html](https://web.mit.edu/kerberos/krb5-1.5/krb5-1.5.4/doc/krb5-admin/Changing-Passwords.html)

* web.mit.edu

* **[Changing Passwords - Kerberos V5 System Administrator's Guid**e](https://web.mit.edu/kerberos/krb5-1.5/krb5-1.5.4/doc/krb5-admin/Changing-Passwords.html)

* Kerberos V5 System Administrator's Guide

#### Check to see if MySQL or MariaDB is installed

dpkg -l | grep -e mysql -e mariadb

#### Remove Ubuntu Unattended Upgrades

* sudo apt-get remove unattended-upgrades && sudo systemctl stop apt-daily.timer && sudo systemctl disable apt-daily.timer && sudo systemctl disable apt-daily.service && sudo systemctl daemon-reload

* cat /etc/apt/apt.conf.d/20auto-upgrades && APT::Periodic::Update-Package-Lists "1"; && APT::Periodic::Unattended-Upgrade "1";

### Find files 1 day old

find . -type f -mtime -1 -printf '%s\n' | awk '{total=total+$1}END{print total/1024000000}'

#### Set Passwords to never expire

$ chage -I -1 -m 0 -M 99999 -E -1 <username>

#### SSH Passphrase Remember
ssh-add ~/.ssh/id_rsa 

## chroot Failed Drive
### Attach data drive with filesystem
$ mount /dev/sdb3 /mnt/drive
### Attach boot director if on seperate partition of drive
$ mount /dev/sdb1 /mnt/drive/boot
$ sudo mount -o bind /proc /mnt/drive/proc
$ sudo mount -o bind /dev /mnt/drive/dev
$ sudo mount -o bind /sys /mnt/drive/sys
$ sudo mount -o bind /run /mnt/drive/run
### chroot into system
$ chroot /mnt/drive

## Clear a log file without deleting it
### redirecti to null
```sh
$ > access.log
```
### cat /dev/null
```sh
$ > access.log
```
### cp /dev/null
```sh
$ cp /dev/null  access.log
```
### dd /dev/null
```sh
$ dd if=/dev/null  of=access.log
```

