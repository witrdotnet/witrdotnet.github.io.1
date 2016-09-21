---
author: admin
comments: false
date: 2013-03-20 08:33:00+00:00
layout: post
link: https://witr.net/quotation/?p=83
slug: connect-with-ssh-from-windows-ssh-secure-shell-to-ubuntu-sshd
title: connect with ssh from windows SSH Secure Shell to ubuntu sshd
wordpress_id: 83
categories:
- ssh
---

March 20, 2013  
  
  
first of all install sshd : "sudo apt-get install openssh-server"  
then start sshd : "sudo /etc/init.d/ssh start" and try to connect from SSH Secure Shell with username/password  
  
If it works, we have to know that username/password authentication is not secure!  
So we will disable authentication with username/password and allow only keys authentication.  
We have to edit sshd config file: sudo vi /etc/ssh/ssh_config  
ensure that lines bellow are not commented and have such values:  
- RSAAuthentication yes  
- PubkeyAuthentication yes  
- AuthorizedKeysFile      %h/.ssh/authorized_keys  
and disable username/password auth:  
- PasswordAuthentication no  
save sshd_config and restart sshd : sudo /etc/init.d/ssh restart  
  
now if you try to connect from SSH Secure Shell with username/password you will be refused. you must generate and put public and private keys.  
  
> ssh-keygen -t dsa mykey.ossh  
will create private and public keys  
  
> cat mykey.ossh.pub >> ~/.ssh/authorized_keys  
will authorize person having keys to login  
  
if you will connect from open ssh client you just have to copy keys in your .ssh home directory  
if you will connect from SSH Secure Shell you must before that convert open ssh keys to ssh2  
> ssh-keygen -e -f mykey.ossh > mykey  
> ssh-keygen -e -f mykey.ossh.pub > mykey.pub  
then use mykey and mykey.pub from SSH SecureShell  
  
connect with specified private key  
> ssh -i path/to/your/private_key user@server.domain_or_ip  
transfer myfile to server  
> scp -i path/to/your/private_key myfile user@server.domain_or_ip:/path_in_server/  
  


