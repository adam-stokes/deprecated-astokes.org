---
layout: post
title: VMWare Server installed as host on FC6
date: 2006-11-09
comments: true
---



If you run into errors related to this :make[1]: Entering directory `/usr/src/kernels/2.6.18-1.2798.fc6-i686' CC [M]  /tmp/vmware-config1/vmnet-only/driver.o CC [M]  /tmp/vmware-config1/vmnet-only/hub.o CC [M]  /tmp/vmware-config1/vmnet-only/userif.o CC [M]  /tmp/vmware-config1/vmnet-only/netif.o CC [M]  /tmp/vmware-config1/vmnet-only/bridge.o CC [M]  /tmp/vmware-config1/vmnet-only/procfs.o/tmp/vmware-config1/vmnet-only/procfs.c:33:26: error: linux/config.h: No such file or directorymake[2]: *** [/tmp/vmware-config1/vmnet-only/procfs.o] Error 1make[1]: *** [_module_/tmp/vmware-config1/vmnet-only] Error 2make[1]: Leaving directory `/usr/src/kernels/2.6.18-1.2798.fc6-i686'make: *** [vmnet.ko] Error 2make: Leaving directory `/tmp/vmware-config1/vmnet-only'Unable to build the vmnet module.That is because config.h does not exist and is being deprecated in 2.6.18-1.2798.fc6 and beyond.To solve this :# touch /usr/src/kernels/2.6.18-1.2798.fc6-i686/include/linux/config.hOnce complete your VMware server should successfully complete vmware-config.pl and you can continue using this product.If it stills fails please see this thread for other ideas : http://www.vmware.com/community/thread.jspa?messageID=501043&amp;#501043



