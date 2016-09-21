---
author: admin
comments: false
date: 2013-04-08 07:28:00+00:00
layout: post
link: https://witr.net/quotation/?p=75
slug: sendxmpp-send-jabber-message-with-command-line
title: 'sendxmpp : send jabber message with command line'
wordpress_id: 75
categories:
- jabber
- linux
- network
---


  
April 8, 2013  
  
  
sendxmpp : send jabber message with command line:  
install sendxmpp (https://www.ebower.com/docs/ubuntu-scripted-gtalk/) : > sudo apt-get install sendxmpp  
create user config file : > touch ~/.sendxmpprc  
secure your configuration file :  > chmod 600 ~/.sendxmpprc  
configure jabber account : > echo 'myusername@gmail.com;talk.google.com mypassword' > ~/.sendxmpprc  
send your first message : > exho "salut" | sendxmpp yourFriend@server
