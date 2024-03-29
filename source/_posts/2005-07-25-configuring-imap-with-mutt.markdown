---
layout: post
title: Configuring imap with mutt
date: 2005-07-25 15:24
comments: true
---

Place this in your ~/.muttrc

``` ini
# This configures mutt to use IMAP(S) server, however, you'll need to
# setup sendmail/postfix/alternative smtp server to enable sending 
# mail out :)
my_hdr From: user@example.com (Joe Blow)
# sets the location for your spool mailbox - 
# the INBOX setting should work on most imap servers
set spoolfile=imaps://mail.server.com/INBOX
# Specifies  the  default  location  of your mailboxes.
set folder=imaps://mail.server.com/
#  Your login name on the IMAP server. 
# Put in a value here to avoid typing in your username 
# each time you start mutt
set imap_user=username
# Specifies the password for your IMAP account.  
# Warning: you should only use this option when you are on 
# a fairly secure machine
# set imap_pass=xyz
# Set this to no to avoid mutt asking you whether you want 
# to move your mail to the local mbox 
set move=no
# If you have more than one mailbox then. 
# This is how long mutt will wait between scanning for 
# incoming mail
set mail_check=60
# Mutt will only scan curently open mailbox for new mail 
# every 10 minutes by default. Set to 15 seconds 
set timeout=15
```
