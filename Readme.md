# Webby
Webby Linux Server Configurator is a web server setup tool for ubuntu & centos linux, you can automate your web server installation without touching the configuration files. You may guess this script is just like Xampp or WampServer; No this script will give you an options of various web server software to install, you can choose one of these web server to install : Apache2, Nginx, Lighttpd, or OpenLiteSpeed.
This script will also help you installing most common web server for a website including FTP server, Database server, Perl and PHP.
This script purpose was helping those PHP/Perl programmers who need a working development environment / true website environment and it hopes with this script they don't need to take their time learning how to setup their own development OSes, but you can also use to setup your web server on the internet. On windows there is an XAMPP, WampServer, EasyPHP, etc; but in Linux you have to do it manually by hand to setup PHP/Perl environment.

# Supported Linux Version
- Ubuntu Server 8.04 ~ 17.04 (32 bit version)
- CentOS 5.0 ~ 7.0 (32 bit version)<br/>

# Installation
Before you can run this webby server setup utility, please make sure you have a working internet connection, and also you have at least Ubuntu 8.04 (Hardy Heron) or CentOS 5.0 installed on your system.
Download the package and log into your linux box and follow these following :

- Uncompress package
   unzip master.zip
- Change permission of setup file
   chmod 755 setup.sh
- Run the setup file
   ./setup.sh

# Uninstallation
You can uninstall all your installed package by using
- ./setup.sh --uninstall

# Unsupported version
## Ubuntu
For an older Ubuntu 8.04 ~ 12.10 version which no longer supported by ubuntu repository, you may install the software by compiling from source code. You need to [download iso cd](http://old-releases.ubuntu.com/releases/) or [download iso dvd](https://mega.nz/#F!tzp2hIKZ!2uGLr-Cko7X11LQKPisCvQ) to install system based packages, then you can use them as apt-cdrom repository.
To make your iso as an apt repository source, follow these steps below :
- Backup your current apt configuration<br/>
shell> mv /etc/apt/source.list
- Make sure your symbolic link /media/cdrom is pointed to the correct cdrom/dvdrom of your iso<br/>
shell> ls -la /media
- Register your mounted iso to apt<br/>
shell> apt-cdrom add
- Update your apt<br/>
shell> apt-get update
- Then install the basic packages<br/>
shell> apt-get install ssh build-essential gcc g++ make unzip

## CentOS
For an older CentOS 5.0 ~ 5.11 version which no longer supported by yum repository, you may install the software by compiling from  source code. You need to download a complete iso from [CentOS Vault](http://vault.centos.org/) and create your own iso yum repository by using these following steps :
- Backup your current yum.repos.d, and remove all files in /etc/yum.repos.d<br/>
shell> tar -zcvf ~/yum-repo-backup.tar.gz /etc/yum.repos.d/*<br/>
shell>rm *.repo
- Prepare your iso cdrom/dvdrom mounting directory (number is the amount of iso files). This example is using CentOS 5.0 cdrom iso which has 6 iso files<br/>
shell> mkdir -p /media/iso/{1,2,3,4,5,6}
- Mount each of iso files<br/>
shell> mount -t iso9660 -o loop ~/CentOS-1of6.iso /media/iso/1<br/>
shell> mount -t iso9660 -o loop ~/CentOS-2of6.iso /media/iso/2<br/>
shell> mount -t iso9660 -o loop ~/CentOS-3of6.iso /media/iso/3<br/>
shell> mount -t iso9660 -o loop ~/CentOS-4of6.iso /media/iso/4<br/>
shell> mount -t iso9660 -o loop ~/CentOS-5of6.iso /media/iso/5<br/>
shell> mount -t iso9660 -o loop ~/CentOS-6of6.iso /media/iso/6
- Install createrepo utility from mounted cdrom iso (CentOS 5.0 is located at iso number 5 of 6 cd)<br/>
shell> cd /media/iso/5<br/>
shell> ls /media/iso/5 | grep createrepo<br/>
shell> rpm -i createrepo-x.x.x.noarch.rpm<br/>
- Clean all your current yum repository cache<br/>
shell> yum clean all
- Register your iso cdrom repos<br/>
shell> cd /media/iso<br/>
shell> createrepo .
- Update your yum cache<br/>
shell> yum update
- Install basic packages for compiling the source code<br/>
shell> yum install gcc gcc-c++ automake autoconf flex bison pkgconfig rpm-build gettext gdb libtool binutils redhat-rpm-config

