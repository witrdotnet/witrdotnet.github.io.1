---
author: admin
comments: false
date: 2015-01-13 10:30:24+00:00
layout: post
link: https://witr.net/quotation/?p=677
slug: mount-remote-file-systems-over-ssh-sshfs
title: mount remote file systems over ssh (sshfs)
wordpress_id: 677
categories:
- ssh
- tricks
---


Mount remote file systems over ssh with three steps:

1. install sshfs


<blockquote>
witr@witr-pc:~$ sudo apt-get install sshfs
</blockquote>


2. create directory where you willi mount your remote file sustem


<blockquote>
witr@witr-pc:~$ sudo mkdir /mnt/witrRemote
</blockquote>


3. finally, mount the remote file system


<blockquote>
witr@witr-pc:~$ sudo sshfs witr@serv.witr.net:myRemoteFolder/ /mnt/witrRemote/
</blockquote>


Assumes myRemoteFolder is on witr serve home directory. See warning bellow.
--------------
**warn :** ~ is expanded by the shell. Paths are relative on sshfs. that means : "sshfs witr@serv.witr.net:**~**/myRemoteFolder ..." will fail with **No such file or directory** error.


