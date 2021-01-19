# express-install-asterisk-in-aws-ec2-linux

```
sed -i 's/\(^SELINUX=\).*/\SELINUX=disabled/' /etc/sysconfig/selinux

sed -i 's/\(^SELINUX=\).*/\SELINUX=disabled/' /etc/selinux/config

reboot

#MAKE SURE SELINUX IS DISABLED running the  next command
#sestatus

yum -y update

yum -y groupinstall core base "Development Tools"

yum install -y make wget openssl-devel ncurses-devel newt-devel libxml2-devel kernel-devel gcc gcc-c++ sqlite-devel libedit-devel libuuid-devel

cd /usr/src/

wget [http://downloads.asterisk.org/pub/telephony/asterisk/asterisk-18-current.tar.gz](http://downloads.asterisk.org/pub/telephony/asterisk/asterisk-18-current.tar.gz)

tar zxvf asterisk*

cd /usr/src/asterisk*

contrib/scripts/install_prereq install


./configure --libdir=/usr/lib64 --with-pjproject-bundled --with-jansson-bundled && make menuselect && make && make install

make samples

touch /etc/redhat-release

make config

ldconfig

rm -f /etc/redhat-release

service asterisk start

systemctl enable asterisk

asterisk -rvvvvvvvvvvvvv

```
