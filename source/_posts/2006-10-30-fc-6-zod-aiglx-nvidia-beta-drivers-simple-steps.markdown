---
layout: post
title: FC 6 (Zod) + AIGLX + Nvidia beta drivers - simple steps
date: 2006-10-30
comments: true
---



Open up a terminal type the following as root :# rpm -ivh http://rpm.livna.org/livna-release-6.rpm# yum install --enablerepo=livna-testing kmod-nvidiaNext switch to runlevel 3# telinit 3# nvidia-config-display enable# telinit 5Next edit /etc/X11/xorg.conf and add the following in the "Device" section:Option      "AddARGBGLXVisuals" "True"Add this to the "Module" section:Load     "extmod"Save and exit, now back to the DE.Finally, select "System" -> "Preferences" -> "Desktop Effects" -> "Enable effects" and enjoy the eye candy.ATI users can just use the 'radeon' driver provided with FC6 and put this in the "Module" section of /etc/X11/xorg.conf:Load   "dri"Not sure how this is hard compared to Ubuntu :\ Must be something in the air.



