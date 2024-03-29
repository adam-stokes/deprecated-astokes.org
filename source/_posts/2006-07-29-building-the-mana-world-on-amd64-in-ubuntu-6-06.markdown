---
layout: post
title: Building The Mana World on AMD64 in Ubuntu
date: 2006-07-29
comments: true
---

**NB**. Ubuntu Precise, Quantal, Raring users may install Manaworld
  with:
  
``` console
apt-get install mana
```

In my experience building tmw for amd64 was pretty straightforward, 
here are the steps for those curious. First setup your repositories 

``` console /etc/apt.sources.list
deb http://bertram.ifrance.com 
deb-src http://bertram.ifrance.com
```

Next build the .deb based packages and install

``` console
sudo apt-get install devscripts fakeroot
apt-get source tmw
cd tmw-VERSION$ sudo apt-get build-dep tmw
debuild -us -uc
sudo dpkg -i ../tmw_VERSION_ARCHITECTURE.deb
../tmw-data_VERSION_ARCHITECTURE.deb
../tmw-music_VERSION_ARCHITECTURE.deb
```

Fedora users:

```console
yum install manaworld
```
