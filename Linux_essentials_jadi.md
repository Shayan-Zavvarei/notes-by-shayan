
### Working with Terminal

We have some general rules in every distributions of linux. 
- `.`: current directory 
- `..`: parent directory
- ~: home
- `mkdir`: make directory
- `rmdir`: remove directory
- `cd`: change directory 
Example: 
```bash
mkdir home/fun
cd home/fun
# This command will make a directory name "fun" in the direction of home/ and. 
# Then cd will change your direcroty to the home/fun
```
- `ls`: show and fine list of directories
- you can open app by typing it's name in the terminal. 
- you can even open  compatible files in the terminal. for example:
```bash
# A basic text edditor in linux ix gedit. so you can open a texf file using gedit in terminal:
gedit myfile.txt
```
- In linux, Switches usually define by `-`
- `ls -l`: show long details  
- `ls -tr`: show logs in reverse time 
- `ls -th`: show logs in human readable
- `ls-ltrh`: this is what we usually use for reading logs in terminal
- `cat`: show contents of a file
- `man`: show the manual of each command
- `cp`: copy file1 over file2
- `touch`: make file but will not open it 
```bash
cp file1.txt file2.txt 
cp file.txt home/shayan/files
```
- `rm`: remove file in your chosen directory
- `mv`: move file1 from your current directory to chosen directory
```bash
mv file.txt /home/chosen/directory
```
example:
```bash
cat ../file.txt
# This will show the content of the file.txt which is in a parent directory from your current directory
```
- `less`: its like `cat` but suitable for long logs page by page with control
- `grep`: grep will show only the lines containts what you want in your logs.
```bash
grep do file.txt
```
- `su`: sets you as a root user so  you don't need to use sudo each time.
- `|`: This is pipe. this will the result of a command to another command after it.
## Separating home from root directory in linux
A linux distro can separate into 3 main partition. root, home and swap.
- `root(\)`: all system files of linux distro will be here.
- `swap`: it is like a virtual memory, when we have lack of ram, some data will go to swap for a while.
- `home(\home)`: all other data will be here.
Each partition has it's own `Mount Point`
In this case you can change your linux distro without changing your/deleting data
- 30 GB for your linux distro - ext4 - `/`
- 8 GB for swap - 
- else for home - ext4 -
you can install a new distro in your `/` without changing or deleting `/home` directory
so for installing new distro you should:
- format `/`
- do not format `/home`
## How to setup a web server using linux
First you need to buy a VPS(Virtual Private Server). it's will distribute a physical server virtually into more that one server for each user. Most VPS services give you:
- OS(windows, Linux, ...)
- Internet access with an IP
- Possibility of installing apps 
### Connecting to a server using `SSH`
Connecting to severs is usually based on ssh protocol. In linux we can use ssh command in terminal:
```bash 
ssh root@<IP-Address>
```
In the first attempt of connecting to server, you need to confirm a fingerprint of server.
#### What should you do after connecting to the server?
For security, you need to do somethings right after connecting to the server:
1. changing the root password using :`passwd` 
2. Update-Upgrade system:
```bash 
# In CentOS:
yum update 
# In Debian/Ubuntu:
apt-get update
apt-get upgrade
# In Arch:
pacman -Syu
```
3. Creating a normal user for doing some normal things without using root:
```bash
useradd <<username>> passwd <<password>>
```
#### Starting the server
Based on your usage, you can use different servers for example:
Nginx, Apache(httpd)

- Installing the sever in centos:
```bash 
yum install httpd
```
- Installing server in Debian/Ubuntu:
```bash 
apt-get install apache2
```
#### Managing the sever
After installing the server, you need to manage the server using `systemd`
- Starting the server:
```bash 
systemctl start httpt
```
- See the status of the server:
```bash 
systemctl status httpd
```
- Activating the server after each boot:
```bash 
systemctl enable httpd
```
#### Firewall configuration 
After initializing the server, due to active firewall on the server, the input request to the sever using port 80(base port of the internet) has been block.
So after first connecting, you need to open this port.
```bash
# Temperorely opens the port 80 of the internet:
firewall-cmd --zone-public --add-port=80/tcp 
# permanantly opens the port 80 of the internet:
firewall-cmd --zone-public --add-port=80/tcp --permanent
```
Then Reload the firewall:
```bash 
firewall-cmd --reload 
```
For enhancing the security of the server, you can do:
1. use a `public_html`
2. Hardening the system and blocking the root access.
3. Connecting a web domain using a DNS
---
###  Connecting personal Domain
Assume you have an domain. in the beginning, you need a domain that you can buy a domain for free from **freedomain.com** 
*It's better to access the server using SSH protocol*
After connecting to server its better to creat a public-html for each user of the server.  all HTML files should e in a same directory.
- Configurations of the apache server is in the below directory:
```bash
etc/httpd --> httpd.conf
# Important: naturatlly for using the user is in the directory: 
home/[user]/public_html
```
#### Challenges with permissions:
for us as  juniours it's better to turn off the `SELinux`. 
```bash
setenforce 0
# OR
cd /etc/selinux/config
SELinux(Enable) --> disable
```
- you need to give access to other users to home directories:
```bash
chmod 755 /home/[username]
public_html chmod 755/home/[username]/public_html
```
---
### FTP and Hardening
For enhancing the security of the server we need to do a little bit hardening. the main goal is to enhance the security of users entry.
*Most important thing for security is to blocking the root entry by using SSH protocol*
```bash
cd /etc/ssh/shhd_config
```
- change the `PermitRootLogin` to `no`
```bash
systemctl restart shhd
```
### Managing the access of the users
- In Linux you can give  access to other users and you can add them to the `sudo` or `wheel` group.
- After that, they can do some commands using `sudo` as root. 
```bash  
usermod -aG [group][username]
```

#### FTP service
FTP(File Transfer Protocol) is a common file transfer service from PC to servers. 
```bash
# 1. Installing the service
yum install vsftpd
# 2. starting the service
systemctl start vsftpd
# 3. activate it after reboot
systemctl enable vsftpd
# Configuration of the vsftpd:
/etc/vsftpd/vsftp.conf/
``` 

*Some important setting in the configurations*
```bash   
anonymous_enable=N0
local_enable=YES
write_enable=YES
```
#### Transfer files from the PC to the server
You can use some apps to transfer files from your pc to the server for example `FileZilla`
**In some linux servers the firewall  is active so you need to open some ports for giving access to the FTP.**
```bash
firewall-cmd --permanant --add-port=21/tcp
firewall-cmd --reload 
firewall-cmd --permanant --add-server=ftp
```
---
### Installing the php and MySQL on the server for wordpress (LAMP)
Here in this section we want to set up a wordpress server using linux terminal based on CentOS distro. 
As usual, we use SSH protocol to connect to the server. 
1. Downloading the wordpress package from the *WordPress.org* as `tar.gz`
2. use wget for download links in the terminal:
```bash
cd \home\<dir you want>
wget <link>
# If you don't have the wget you can:
yum install wget
```
3. unzip (untar) the compressed file using `tar`
```bash 
tar xvf <fil>
```
4. Move the files you decompressed to the directory of the appache server as Document Root.
5. Configuration of the Apache server:
```bash
etc/httpd/conf
```
6. Install an activation of the php:
```bash 
yum install php
# To activate the php on the server:
systemctl restart httpd
```
7. Installation of the necessary Extensions to connect php to MySQL: you need to install packages like (php-mysql)
```bash
yum search php
# use:
grep
yum install php-mysql
systemctl restart httpd
```
8. Installation of the MySQL as a data container
```bash
mysql -u root -p
```
9. Create Database: 
```bash 
CREATE DATABASE weblog 
SHOW DATABASES
use weblog
```
#### NEW users, NEW access
```bash
GRANT ALL PRIVILEGES ON weblog.* TO 'webloguser'@'localhost' IDENTIFIED BY; '!'PasswordGhadimatGhavi
```
For activating this user on the server you need to flush:
```bash 
FLUSH PRIVILEGES
```

### Compile Kernel of Linux  
Kernel is a  software to connect each hardware to operating system.
Steps of downloading kernel and installing it is:
1.  Downloading Kernel source from `kernel.org`
2. kernel compilers like gcc and make
3. make directory for kernel with suitable name `build`
4. clean the directory of the build for example `.make mrproprt`
5. 































































































































































