__1.0__ To begin building this website, I registered dittoip.com at [[Cloudflare Registrar|https://www.cloudflare.com/products/registrar/]].  
__2.0__ Setup Ubuntu Server 24.04 minimal.  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;__2.1__ Login and verify Ubuntu version:  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`:~$ more /etc/issue`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`Ubuntu 24.04.4 LTS \n \l`  
__3.0__ Setup a new user account (ditto in this case):  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`:~$ more /etc/issue`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`:~$ sudo adduser --disabled-password --gecos "" ditto`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`info: Adding user 'ditto' ...`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`info: Selecting UID/GID from range 1000 to 59999 ...`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`info: Adding new group 'ditto' (1002) ...`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`info: Adding new user 'ditto' (1002) with group 'ditto (1002)' ...`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`info: Creating home directory '/home/ditto' ...`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`info: Copying files from '/etc/skel' ...`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`info: Adding new user 'ditto' to supplemental / extra groups 'users' ...`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`info: Adding user 'ditto' to group 'users' ...`  
__3.1__ Verify that user ditto exists:  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`:~$ id ditto`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`uid=1002(ditto) gid=1002(ditto) groups=1002(ditto),100(users)`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;__3.2__ Add ditto to the sudo group then verify:  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`:~$ sudo usermod -aG sudo ditto`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`:~$ id ditto  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`uid=1002(ditto) gid=1002(ditto) groups=1002(ditto),27(sudo),100(users)`  




&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;__3.3__ Give ditto a password:  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`:~$ sudo passwd ditto`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`New password:`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`Retype new password:`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`passwd: password updated successfully`  
