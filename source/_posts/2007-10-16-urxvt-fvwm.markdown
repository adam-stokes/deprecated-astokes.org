---
layout: post
title: urxvt, fvwm
date: 2007-10-16
comments: true
---



Some lost configuration items I've missed for awhile and finally brought back -- one being tabbed windows in urxvt. You can install urxvt (rxvt-unicode) with the following :# yum install rxvt-unicodeTake a look at my Xfdefaults and note the !perl modules section for how to load the tabbed perl extension or you may load it manually with :# urxvt -pe /usr/lib/urxvt/perl/tabbedIf any of you are wondering about the bottom thats my .screenrc config.I've also spent some time altering fvwm, a lot of the theming so far has come from taviso's work which has helped me quite a bit in learning all that fvwm has to offer.I've done some updating and alterations to Chris Snook's original hangwatch application which basically does some small code cleanup and provides the options to daemonize the application by default and of course run in the foreground. You can pick up the updated application on my people page. I will be packaging it shortly along with creating necessary initscripts for easy initialization.There is another big project im working on as well which basically strips a fingerprint from a vmcore off a kernel panic and matches up debug symbols and correct architecture based on a fingerprint database that was generated on over 6000 kernels : ) Once I've packaged it and cleaned up the configuration aspect a bit I do plan on releasing it to the public. The application is split into client/server model (somewhat) where the backend is custom and the fronted is a pylons application (all written in python). The purpose of this was to provide a simple and easy way to create a environment for analyzing and debugging core dumps with the vmcore tool crash.I've made a few contributions to sosreport I highly suggest using this application for any type of system wide data gathering.Finally, my fvwm screenshot : )Oh, on the xbox front I've been playing Bioshock heavily -- I haven't quite gotten into the Halo 3 scene yet and honestly don't know if I will : (, but Bioshock is awesome and if you haven't played it yet I suggest renting it or do like me and buy the damn thing its worth it : )



