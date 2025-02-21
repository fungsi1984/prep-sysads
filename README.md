### check sha iso
- echo "fa95fb748b34d470a7cfa5e3c1c8fa1163e2dc340cd5a60f7ece9dc963ecdf88 \
*ubuntu-21.04-desktop-amd64.iso" | shasum -a 256 --check

### update grub
- fedora, sudo grub2-mkconfig -o /boot/grub2/grub.cfg
- ubuntu, sudo grub-mkconfig -o /boot/grub/grub.cfg
- update, sudo update-grub

### fail boot, just grub interface
- grub> set pager=1
- grub> ls
- find boot file
- grub> ls (hd0,3)
- grub> ls (hd0,2)/
- grub> ls (hd0,2)/boot
- grub> set root=(hd0,2)
- grub> linux /boot/vmlinuz-5.3.18-lp152.57-default root=/dev/sda2
- grub> initrd /boot/initrd-5.3.18-lp152.57-default
- grub> boot

### check ip address
- ip addr show

### check process
- ps -ef
- pstree -p
- ps -eo pid,user,stat,comm

### check services
- systemctl > /tmp/systemctl-units.txt
- better view, systemctl list-unit-files --type=service
- systemctl list-unit-files --type=service --state=enabled
- systemctl list-unit-files --type=service --state=disabled
- systemctl list-unit-files --type=service --state=static

### systemctl stuff
- systemctl status mariadb.service
- sudo systemctl start mariadb.service

### troublesome processes
- sudo systemctl kill mariadb
- nuclear stop, sudo systemctl kill -9 mariadb
- use pid, sudo kill 1234
- nuclear stop, sudo kill -9 1234

### user uid and gid
- id
- ls -l /usr/bin/passwd

### create user 
- sudo useradd test1
- id test1
- sudo ls -a /home/test1/
- sudo passwd test1
- reset password for first login, sudo passwd -e test1
- create private group, sudo useradd -mU test2
- adding user to existing group, sudo useradd -G group1,group2,group3 test1
- -c, --comment accepts any text string. Use this for the user’s full name, or any
comment or description:
  - $ useradd -G group1,group2,group3 -c 'Test 1,,,,' test1

- add web user into development
  - sudo usermod -aG development webUser
- add web into multiple groups
  - sudo usermod -aG frontend,backend,infra webUser


### create group
- create group
  - sudo addgroup infrastructure

- create new system
  - sudo addgroup --system infrastructure

### trouble some user account
- disable account without delete, make it expire
  - sudo passwd -l webUser

- unlock account
  - sudo passwd -u webUser

- disable a user account
  - sudo usermod --expiredate 1 webUser 

- restore account
  - sudo usermod --expiredate -1 webUser

- delete user
  - sudo userdel webUser

- delete user with home directory with contents
  - sudo userdel -r webUser
  
### delete user in ubuntu
- using deluser
  - sudo deluser webUser

- sudo deluser --remove-all-files --backup webUser

- sudo deluser --remove-all-files --backup-to /user-backups webUser

### page 119

### continue from pages 164

### backup with cp
- copies from entire directory
  - cp -auv ~ /media/duchess/2tbdisk/backups/

- choose directory for copies from 
  - cp -auv /home/duchess/* /media/duchess/2tbdisk/backups/

- Create a personal cron job to run your backup every night at 10:30 P.M.:
  - $ crontab -e

```
  # m h dom mon dow   command
  30 22 *   *   *     /bin/cp -au /home/duchess /media/duchess/2tbdisk/backups/
```

### backup using rsync
- rsync -av ~ /media/duchess/2tbdisk/


### rsync with ssh
- rsync -av ~/Music/arias empress@laptop:songs/

### crontab rsync
```
example makes a backup of /etc every night at 10 P.M. to a LAN server named server1:
# m h dom mon dow user command
00 22 * * * root /usr/bin/rsync -a /etc server1:/system-backups
```

### rsync exclude
- rsync -av --exclude=lho-perduta.wav ~/Music/arias /media/duchess/2tbdisk/duchess/Music/

### rsync limit
- rsync --bwlimit=512 -ave ssh ~/Music/arias empress@laptop:songs/




























## Notes
- book, linux cookbook essential skills for linux users and system network administrators


