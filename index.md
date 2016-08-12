---
layout: page
title: Random stuff
---

### Building lighttpd for rapspberry pi on Ubuntu 14.04

#### Setup cross compiler
```
sudo apt-get install -y build-essential g++-arm-linux-gnueabihf gdb-multiarch
```

#### Download lighttpd source
```
mkdir lighttpd
cd lighttpd/
wget http://download.lighttpd.net/lighttpd/releases-1.4.x/lighttpd-1.4.41.tar.gz
tar -xvzf lighttpd-1.4.41.tar.gz
cd lighttpd-1.4.41/
```

#### Setup install directory
We want to install lighthttp in /opt/dev, so create directory and change ownership
```
sudo mkdir /opt/dev/
sudo chown ubuntu:ubuntu /opt/dev/
mkdir /opt/dev/lighttpd
```

#### Build
```
./configure -prefix=/opt/dev/lighttpd -host=arm-linux-gnueabihf CC=arm-linux-gnueabihf-gcc RANLIB=arm-linux-gnueabihf-ranlib STRIP=arm-linux-gnueabihf-strip --without-zlib --without-bzip2 --without-pcre
make
echo $?
make install
```

#### Run
```
/opt/dev/lighttpd/sbin/lighttpd -f lighttpd.conf
```
