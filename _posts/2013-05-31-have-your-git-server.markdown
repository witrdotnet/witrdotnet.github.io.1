---
author: admin
comments: false
date: 2013-05-31 06:59:00+00:00
layout: post
link: https://witr.net/quotation/?p=55
slug: have-your-git-server
title: have your GIT server
wordpress_id: 55
categories:
- git
---


  
=========================================== 31/05/2013  
GIT:  
Consists of two repository. one on server side and the other in client side (clone of server side repos).  
When client commits, modifications were saved to client side repository  
To send modifications to server, client must push commits.  
  
1. install and configure git server  
2. create server git repository  
3. access to remote git repo with eclipse  
4. explore git repository with gitk  
  
1. install and configure git server:  
sudo apt-get install git-core  
git config --global color.diff auto  
git config --global color.status auto  
git config --global color.branch auto  
git config --global user.name "mabrouk"  
==> see your config in vim ~/.gitconfig  
  
2. create server git repository  
cd /home/mba  
mkdir mbaGitRepo  
cd mbaGitRepo  
git init --bare  
  
3. access to remote git repo with eclipse  
Window->Show View->git Repositories  
click on icon "Clone a Git Repository and add the clone to this view"  
- Host : your host  
- Repository path : ~/mbaGitRepo  
- Conection : Protocol ssh / Port 22  
- user: linux username (mba)  
- password : linux user password  
click Next  
don't worry of warning : Source Git repository is empty  
click Next  
Directory : Choose where you want clone the remote git repository in your local machine  
click Finish  
  
4. explore git repository with gitk  
install gitk : sudo apt-get install gitk  
launch gitk  : gitk  


  




