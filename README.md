# Redhat 8 Administration II (Webinar) 

## Grep ##

cat /etc/selinux/config | grep -v -e "^#" -e "^$"

## Anacron 

https://www.thegeekdiary.com/centos-rhel-anacron-basics-what-is-anacron-and-how-to-configure-it/

## Script 

```
# code of simple hello.sh script 
# how to source configuration file properly (no matter where you execute hello.sh
# /usr/local/bin/hello.sh 
#!/bin/bash

cd $(dirname $0)
source config.sh

echo $LOGFILE

echo "Hello World!" > /var/log/test.log
echo "naechste Zeile" >> /var/log/test.log


if [ -z $a"" ]
then
  exit 1
fi

exit 0


```

## Formatting 

- Hint from digitalocean 
- https://www.dropbox.com/s/zqhkuj1bksje11s/Screenshot%202020-04-27%2007.06.57.png?dl=0`

## ACL's 

### General 

- ls -l zeigt nach den standard Rechten ein + welches zeigt, dass ACL vorhanden sind.
- mv übernimmt standardmässig die ACL
- cp kopiert die ACL wenn die Option -p (preserve) angegeben wurde

### Commands

```
setfacl -m <ACL-SPEC>
# setzen / modifizieren von ACL.
setfacl -M <Quelledatei> <Datei oder Ordner>
# setzen / modifizieren von ACL.
setfacl -x <ACL-SPEC> <Datei oder Ordner>
# ACL entfernen.
setfacl -X <Quelledatei> <Datei oder Ordner>
# ACL entfernen.
setfacl -b <Datei oder Ordner>
# Alle ACL-Enträge entfernen.
setfacl -k <Ordner>
# Alle Default acl löschen
```

### Examples 

```
# Set permissions for a specific group 
# recursive / add or modfify for group consultants 
setfacl -Rm g:consultants:rwX /shares/content

# Withdraw permissions for a specific user 
setfacl -Rm u:consultant1:- /shares/content

# Set default permission for a specific group 
# important for the subdirectories and the content of them
setfacl -m d:g:consultants:rwx /shares/content

```

### SELinux 

```
# Add context permanently 
[root@rh1a html]# mkdir /virtual 
[root@rh1a html]# touch /virtual/index.html
[root@rh1a html]# ls -laZ /virtual/index.html 
-rw-r--r--. 1 root root unconfined_u:object_r:default_t:s0 0 Apr 27 13:30 /virtual/index.html
[root@rh1a html]# semanage fcontext -a -t httpd_sys_content_t '/virtual(/.*)?'
```

### libvirt / Virtuelle Maschinen 

```
#Network needs to beinstalled /default
yum install libvirt-daemon-config-network
```


## Bash Advanced Scripting 
https://tldp.org/LDP/abs/html/
