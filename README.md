I am a network consultant and a full stack developer.  I like to involve myself in emerging technologies and ideas that elevate humanity.
* Read my notes at http://dittoip.com
* Send me ideas for collaboration at hle@dittoi.com
```
!!!1.0 To begin building this website, I registered dittoip.com at [[Cloudflare Registrar|https://www.cloudflare.com/products/registrar/]].
!!!2.0 Setup Ubuntu Server 24.04 minimal.
*2.1 Login and verify Ubuntu version:
**`:~$ more /etc/issue
Ubuntu 24.04.4 LTS \n \l`
!!!3.0 Setup a new user account (ditto in this case):
*`:~$ sudo adduser --disabled-password --gecos "" ditto
info: Adding user 'ditto' ...
info: Selecting UID/GID from range 1000 to 59999 ...
info: Adding new group 'ditto' (1002) ...
info: Adding new user 'ditto' (1002) with group 'ditto (1002)' ...
info: Creating home directory '/home/ditto' ...
info: Copying files from '/etc/skel' ...
info: Adding new user 'ditto' to supplemental / extra groups 'users' ...
info: Adding user 'ditto' to group 'users' ...`
*3.1 Verify that user ditto exists:
**`:~$ id ditto
uid=1002(ditto) gid=1002(ditto) groups=1002(ditto),100(users)`
*3.2 Add ditto to the sudo group then verify:
**`:~$ sudo usermod -aG sudo ditto`
**`:~$ id ditto
uid=1002(ditto) gid=1002(ditto) groups=1002(ditto),27(sudo),100(users)`
*Give ditto a password:
**`:~$ sudo passwd ditto
New password: 
Retype new password: 
passwd: password updated successfully`
!!!4.0 Re-login as the new user (ditto in this case), now that this user has privileges to install globally.
!!!5.0 Change to the home directory (/home/ditto in this case) and verify:
*`:~$ cd ~`
*`:~$ pwd
/home/ditto`
!!!6.0 Verify that the server has at least one publicly routable IP address.
*Non-routable IP addresses:
**10.0.0.0/8 (RFC 1918)
**100.64.0.0/10 (RFC 6598)
**172.16.0.0/12 (RFC 1918)
**192.168.0.0/16 (RFC 1918)
**127.0.0.0/8, (loopback)
**169.254.0.0/16 (link-local)
**224.0.0.0/4 (multicast)
*`:~$ ip a | grep -w inet
inet 127.0.0.1/8 scope host lo
inet 107.173.104.108/27 brd 107.173.104.127 scope global eth0`
!!!7.0 Log back into [[Cloudflare Registrar|https://www.cloudflare.com/products/registrar/]]. Add a DNS record for dittoip.com to the routable IP.
*Type: A
*Name: dittoip.com
*IPv4: 107.173.104.108
*TTL: 300
!!!8.0 Update and upgrade Ubuntu with the sudo user (ditto in this case).
*`:~$ sudo apt update
Get:1 http://security.ubuntu.com/ubuntu noble-security InRelease [126 kB]
Hit:2 http://archive.ubuntu.com/ubuntu noble InRelease
Get:3 http://archive.ubuntu.com/ubuntu noble-updates InRelease [126 kB]
...
Fetched 10.6 MB in 5s (2,036 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
7 packages can be upgraded. Run 'apt list --upgradable' to see them.`
*`:~$ apt list --upgradable
Listing... Done
libssh-4/noble-updates,noble-security 0.10.6-2ubuntu0.4 amd64 [upgradable from: 0.10.6-2ubuntu0.3]
...
xxd/noble-updates,noble-security 2:9.1.0016-1ubuntu7.10 amd64 [upgradable from: 2:9.1.0016-1ubuntu7.9]`
*`:~$ sudo apt upgrade -y
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  libssh-4 python3-cryptography vim vim-common vim-runtime vim-tiny xxd
...
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 standard LTS security updates
Need to get 11.4 MB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 vim amd64 2:9.1.0016-1ubuntu7.10 [1,882 kB]
...
Fetched 11.4 MB in 1s (7,658 kB/s)
(Reading database ... 160693 files and directories currently installed.)
Preparing to unpack .../0-vim_2%3a9.1.0016-1ubuntu7.10_amd64.deb ...
Unpacking vim (2:9.1.0016-1ubuntu7.10) over (2:9.1.0016-1ubuntu7.9) ...
...
Setting up vim-tiny (2:9.1.0016-1ubuntu7.10) ...
Processing triggers for libc-bin (2.39-0ubuntu8.7) ...
Processing triggers for man-db (2.12.0-4build2) ...
Scanning processes... 
Scanning linux images... 
Pending kernel upgrade!
Running kernel version:
  6.8.0-101-generic
Diagnostics:
  The currently running kernel version is not the expected kernel version 6.8.0-106-generic.
Restarting the system to load the new kernel will not be handled automatically, so you should consider rebooting.
No services need to be restarted.
No containers need to be restarted.
No user sessions are running outdated binaries.
No VM guests are running outdated hypervisor (qemu) binaries on this host.`
!!!9.0 Reboot to load kernel version 6.8.0-106-generic
*`:~$ sudo init 6
Broadcast message from root on pts/1 (Tue 2026-03-17 14:47:37 UTC):
The system will reboot now!`
*`:~$ cat /proc/version
Linux version 6.8.0-106-generic (buildd@lcy02-amd64-074) (x86_64-linux-gnu-gcc-13 (Ubuntu 13.3.0-6ubuntu2~24.04.1) 13.3.0, GNU ld (GNU Binutils for Ubuntu) 2.42) #106-Ubuntu SMP PREEMPT_DYNAMIC Fri Mar  6 07:58:08 UTC 2026`
!!!10.0 Install Node.js and npm
*`:~$ sudo apt install nodejs npm`
!!!11.0 Install TiddlyWiki current release (5.3.8)
*`:~$ sudo npm install -g tiddlywiki`
!!!12.0 Create an empty wiki called dittoip in the home folder:
*`:~$ cd ~`
*`:~$ tiddlywiki dittoip --init server`
!!!13.0 Add website users editor1 and editor2:
*`:~$ echo "username,password" > ~/dittoip/users.csv`
*`:~$ echo "editor1,editpass1" >> ~/dittoip/users.csv`
*`:~$ echo "editor2,editpass2" >> ~/dittoip/users.csv`
!!!14.0 Install nginx web services
*`:~$ sudo apt install nginx`
!!!15.0 Configure the proxy server for dittoip.com:
*`:~$ sudo nano /etc/nginx/sites-available/dittoip.com`
```
server {
    server_name dittoip.com
    client_max_body_size    100M;

    location / {
    proxy_pass   http://127.0.0.1:8080;
    proxy_set_header        Host             $host;
    proxy_set_header        X-Real-IP        $remote_addr;
    proxy_set_header        X-Forwarded-For  $proxy_add_x_forwarded_for;
    }
}
```
!!!16.0 Enable proxy for dittoip.com:
*`:~$ sudo ln -s /etc/nginx/sites-available/dittoip.com /etc/nginx/sites-enabled`
!!!17.0 Encrypt dittoip.com with Let's Encrypt:
*`:~$ sudo apt install certbot python3-certbot-nginx`
*`:~$ sudo certbot --nginx`
!!!18.0 Start this website so that only editor1 and editor2 have editing privileges:
*`:$ /usr/local/bin/tiddlywiki /home/ditto/dittoip --listen credentials=users.csv "readers=(anon)" "writers=(authenticated)"`
```
