---
layout: post
title: Ubuntu Netinstall
date: 2006-09-14
comments: true
---

Hmm I just had a very good experience with one of my machines with no floppy, cdrom, usb drives and only a PXE capable ethernet card using this quick Ubuntu netinstall guide. This took about 15 minutes to setup and didn't have to fuss with configuring an entire dhcp server for the job.Update: FC5 has dnsmasq in its extras repo.# yum install dnsmasqThe above article should apply other than running tftpd through xinetd rather than a standalone daemon.
