---
layout: post
title: Fedora 8, Thinkpad T61, fingerprint authentication
date: 2008-02-20
comments: true
---



Using a T61 or any IBM laptop that has the fingerprint scanner install the package thinkfinger :# yum install thinkfingerAdd your user:# su -# tf-tool --add-user adamSwipe your finger 3 times.Alter /etc/pam.d/system-auth to include the think_finger pam module. Mine looks like :#%PAM-1.0# This file is auto-generated.# User changes will be destroyed the next time authconfig is run.auth        required      pam_env.soauth        sufficient    pam_thinkfinger.soauth        sufficient    pam_unix.so nullok try_first_passauth        requisite     pam_succeed_if.so uid >= 500 quietauth        required      pam_deny.soaccount     required      pam_unix.soaccount     sufficient    pam_localuser.soaccount     sufficient    pam_succeed_if.so uid account     required      pam_permit.sopassword    requisite     pam_cracklib.so try_first_pass retry=3password    sufficient    pam_unix.so md5 shadow nullok try_first_pass use_authtokpassword    required      pam_deny.sosession     optional      pam_keyinit.so revokesession     required      pam_limits.sosession     [success=1 default=ignore] pam_succeed_if.so service in crond quiet use_uidsession     required      pam_unix.soOnce complete logout of Gnome, and attempt to login by clicking or typing your associated user name and then swipe your finger :)



