---
author: admin
comments: false
date: 2015-01-12 11:35:00+00:00
layout: post
link: https://witr.net/quotation/?p=671
slug: guess-ssh-key-passphrase
title: guess ssh key passphrase
wordpress_id: 671
categories:
- ssh
- tricks
---


You have probably forgotten your ssh key passphrase. But you have a hunch what it might be. The simple way to check it, is to use **ssh-keygen** with **-y** argument which read private key file and print public key :


<blockquote>
witr@witr-pc:~$ ssh-keygen -y
Enter file in which the key is (/home/witr/.ssh/id_rsa): /tmp/my_private_ssh_key
Enter passphrase:
</blockquote>



If you input the correct passphrase, it will show you the associated public key. Otherwise, it will display


<blockquote>
load failed
</blockquote>



