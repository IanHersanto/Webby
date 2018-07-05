# [Webby](https://ianhersanto.github.io/Webby/index.html)
### Small linux bash utility to build and prepare web server of your choice
[![HitCount](http://hits.dwyl.io/IanHersanto/Webby.svg)](http://hits.dwyl.io/IanHersanto/Webby)
[![license](https://img.shields.io/github/license/mashape/apistatus.svg)](https://opensource.org/licenses/MIT)<br/><br/>
Webby Linux Http Server Installation Wizard is a web server configuration tool for Ubuntu, Debian, RHEL, Centos, and Fedora linux. You can automate your web server installation without touching the configuration files or even experiencing compilation error. You may guess this script is just like Xampp or WampServer; No this script will give you an options of various web server software to install, you can choose one of these web server to install : Apache2, Nginx, Lighttpd, OpenLiteSpeed, Cherokee, Hiawata, or Monkey web server.
Officially webby is written to help PHP/Perl programmers who need a working development environment / true website environment and it hopes with this utility they don't need to take their time learning how to setup their own development OSes, but with webby you can also to use it to setup your own unmanaged vps/dedicated web server on the internet. On windows there is an XAMPP, WampServer, EasyPHP, etc; but in Linux you have to do it manually by hand to setup Web Server, Database, FTP, and PHP/Perl environment.

## Supported Linux Version (checked for testing progress)
- [x] [Ubuntu Server](http://old-releases.ubuntu.com/releases/) 8.10 ~ 18.04 (32 bit version)
- [ ] [CentOS](http://archive.kernel.org/centos-vault/) 6.0 ~ 7.x (32 bit version)
- [ ] [Fedora](https://archives.fedoraproject.org/pub/archive/fedora/linux/releases/) 9 ~ 26 (32 bit version)
- [ ] [Redhat Enterprise](https://developers.redhat.com/products/rhel/download/) 6.0 ~ 7.x (32 bit version)
- [ ] [Debian](https://cdimage.debian.org/mirror/cdimage/archive/) 5.0 ~ 9.3 (32 bit version)

The OS version above is using standard package distribution of minimum software tool requirements, but you can also use the below version of what is mentioned above by updating your software tools to meet these minimum requirements below :
<br/>

## Minimum Requirements
- Linux kernel 2.6.25
- Perl 5.10.0
- Wget 1.17.1 (optional)
- Glibc 2.8.90
- Bash 3.2.39

## Recommended Requirements
- Linux kernel 3.13
- Perl 5.14
- Wget 1.16
- Glibc 2.15
- Bash 4.2

## Installation
Before you can run this utility, please make sure you have a working internet connection, and also you have at least Ubuntu 8.10, Debian 5.0, CentOS 6.0, RHEL 6.0, or Fedora 9 installed on your system.

## Parameters 
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Parameter&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Description |
| --- | --- |
| \-u \| \-\-uninstall | Uninstall packages (parameter : all, skipdb, skipdata)<br/>all&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;: uninstall http server, web documents,ftp, mysql or postgresql.<br/>skipdb&nbsp;&nbsp;&nbsp;&nbsp;: uninstall http server, web documents, ftp but skip database server(if any).<br/>skipdata&nbsp;: uninstall http server and ftp only, and will keep web documents and database server.|
| \-d \| \-\-dir | Install Webby to your own defined path |
| \-i \| \-\-install\-legacy | If you run an older OS release please make sure to still have your OS installation cd/dvd mounted on tray, because it will required to install default software packages from cd/dvd installer. |
| \-g \| \-\-get\-src | Download a set of source codes of a web server, database, php, and ftp package. This will download software with its dependency libraries. Example package name :<br/><br/> apache-2.4.29, nginx-1.12.2, lighttpd-1.4.49, litespeed-1.3.30,<br/>mysql-5.5.59, postgresql-10.3, mariadb-10.2.14, mongodb-3.4.14,<br/>php-5.6.34, proftpd-1.3.6, pureftpd-1.0.47, etc |
| \-a \| \-\-skip\-repo\-update | Skip repository update (This will assume that your apt/yum/dnf repository list already updated). |
| \-c \| \-\-custom\-repo | Define your custom OS repository url.<br/>example :<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;webby -c http://old-releases.ubuntu.com/ubuntu/ |
| \-x \| \-\-copy | Copy current webby script file to remote server<br/>Example :<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;webby -x user@192.168.0.1 |
| \-s \| \-\-skip\-net\-test | Skip internet connection checking. But this will require OS installation cd/dvd. |
| \-r \| \-\-remove\-update | Remove wget upgrade and set back to original cd/dvd legacy. |
| \-v \| \-\-verify\-source | Its recommended that you run this before installation to make sure that the source code still remain the same from developer (match to built state as used and tested on webby). You may cancel your installation if any new modification from developer could causing new bugs. |
| \-q \| \-\-setup | Quick mode download & install web server of your choice, you can see available web server versions from ext/ folder. The package name used here is same as --get-src naming term.<br/><br/>apache-x.x.x	: download & install apache packages<br/>nginx-x.x.x		: download & install nginx packages<br/>lighttpd-x.x.x	: download & install lighttpd packages<br/>litespeed-x.x.x	: download & install openlitespeed packages<br/>mysql-x-x-x	: download & install mysql packages<br/>php-x-x-x  : download & install php packages<br/>etc |

## Unsupported version
### Ubuntu
For an older Ubuntu 8.10 ~ 12.10 version which no longer supported by ubuntu repository, you may install the software by compiling from source code. You need to [download iso cd](http://old-releases.ubuntu.com/releases/) or [download iso dvd](https://mega.nz/#F!tzp2hIKZ!2uGLr-Cko7X11LQKPisCvQ) to install system based packages, then you can use them as apt-cdrom repository.
To make your iso as an apt repository source, follow these steps below :
- Backup your current apt configuration<br/>
shell> mv /etc/apt/source.list
- Make sure your symbolic link /media/cdrom is pointed to the correct cdrom/dvdrom of your iso. This should be pointing to /media/cdrom -> /media/cdrom0 -> /dev/sr0<br/>
shell> ls -la /media
- Register your mounted iso to apt<br/>
shell> apt-cdrom -d /media/cdrom add
- Update your apt<br/>
shell> apt-get update
- Then install the basic packages<br/>
shell> apt-get install ssh build-essential gettext libtool m4 autoconf gcc g++ usbutils make unzip

### Fedora / CentOS / RHEL
For an older Fedora 9 version which no longer supported by yum repository, you may install the software by compiling from  source code. You need to download a complete iso from [Fedora Archive](https://archives.fedoraproject.org/pub/archive/fedora/linux/releases/) and create your own iso yum repository by using these following steps :
- Create directories for mounting iso files and backup your current yum.repos.d, then remove all files in /etc/yum.repos.d<br/>
shell> mkdir -p /media/repo-cd/{1,2,3,4,5,6}<br/> 
or<br/>
shell> mkdir -p /media/repo-dvd <br/>
shell> tar -czvf ~/repo-backup.tar.gz /eetc/yum.repos.d/fedora*.repo<br/>
shell> rm -f /etc/yum.repos.d/*<br/>
- Mount each of iso files<br/>
shell> mount -t iso9660 -o loop ~/Fedora-9-disc1.iso /media/repo-cd/1<br/>
shell> mount -t iso9660 -o loop ~/Fedora-9-disc2.iso /media/repo-cd/2<br/>
shell> mount -t iso9660 -o loop ~/Fedora-9-disc3.iso /media/repo-cd/3<br/>
shell> mount -t iso9660 -o loop ~/Fedora-9-disc4.iso /media/repo-cd/4<br/>
shell> mount -t iso9660 -o loop ~/Fedora-9-disc5.iso /media/repo-cd/5<br/>
shell> mount -t iso9660 -o loop ~/Fedora-9-disc6.iso /media/repo-cd/6<br/>
- Make entry to /etc/fstab to mount iso files at boot<br/>
shell> echo "/home/user-dir/Fedora-9-disc1.iso    /media/repo-cd/1         udf,iso9660 user,loop     0 0" >> /etc/fstab<br/>
shell> echo "/home/user-dir/Fedora-9-disc2.iso    /media/repo-cd/2         udf,iso9660 user,loop     0 0" >> /etc/fstab<br/>
shell> echo "/home/user-dir/Fedora-9-disc3.iso    /media/repo-cd/3         udf,iso9660 user,loop     0 0" >> /etc/fstab<br/>
shell> echo "/home/user-dir/Fedora-9-disc4.iso    /media/repo-cd/4         udf,iso9660 user,loop     0 0" >> /etc/fstab<br/>
shell> echo "/home/user-dir/Fedora-9-disc5.iso    /media/repo-cd/5         udf,iso9660 user,loop     0 0" >> /etc/fstab<br/>
shell> echo "/home/user-dir/Fedora-9-disc6.iso    /media/repo-cd/6         udf,iso9660 user,loop     0 0" >> /etc/fstab<br/>
- Auto mount for each iso at user login<br/>
shell> echo "mount /media/repo-cd/1" >> ~/.bashrc<br/>
shell> echo "mount /media/repo-cd/2" >> ~/.bashrc<br/>
shell> echo "mount /media/repo-cd/3" >> ~/.bashrc<br/>
shell> echo "mount /media/repo-cd/4" >> ~/.bashrc<br/>
shell> echo "mount /media/repo-cd/5" >> ~/.bashrc<br/>
shell> echo "mount /media/repo-cd/6" >> ~/.bashrc<br/>
- Create file /etc/yum.repos.d/fedora-cd.repo and fill with<br/>
shell> nano /etc/yum.repos.d/fedora-cd.repo

       [fedora-cd]
       name=Fedora $releasever - $basearch - Updates
       failovermethod=priority
       baseurl=file:///media/repo-cd/1
               file:///media/repo-cd/2
               file:///media/repo-cd/2
               file:///media/repo-cd/3
               file:///media/repo-cd/4
               file:///media/repo-cd/5
               file:///media/repo-cd/6
       enabled=1
       gpgcheck=1
       gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-fedora-$basearch

- Update your yum cache<br/>
shell> yum update<br/>
- Install basic packages for compiling the source code<br/>
shell> yum install gcc gcc-c++ automake autoconf flex bison pkgconfig rpm-build gettext gdb libtool binutils redhat-rpm-config

