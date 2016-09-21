---
author: admin
comments: false
date: 2014-09-11 09:53:50+00:00
layout: post
link: https://witr.net/quotation/?p=594
slug: when-ssh-connection-refused-with-too-many-authentication-failures-for-x
title: when ssh connection refused with "Too many authentication failures for x"
wordpress_id: 594
categories:
- ssh
---


If you are here you have probably got following message when trying to connect with ssh:
"Received disconnect from xx.xx.xxx.xx: 2: Too many authentication failures for x"

In fact, when trying to connect, ssh send all locally registred keys to the server trying them one by one. The server will reject any key after too many keys have been rejected.

If you are using key to connect try : 


<blockquote>ssh -i your_key -o 'IdentitiesOnly yes' user@server:/path/</blockquote>


If you are connecting without keys (login and password only) try


<blockquote>ssh -o 'IdentitiesOnly yes' user@server:/path/</blockquote>




