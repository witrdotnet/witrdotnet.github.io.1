---
author: admin
comments: false
date: 2015-04-03 22:53:33+00:00
layout: post
link: https://witr.net/quotation/?p=827
slug: access-to-a-dockerized-apache-from-local-mochine
title: access to a dockerized apache from local mochine
wordpress_id: 827
categories:
- docker
---


Get ubuntu


<blockquote>docker pull ubuntu:vivid</blockquote>


Start ubuntu container


<blockquote>docker run -ti ubuntu:vivid /bin/bash</blockquote>


Install apache


<blockquote>root@54a954be4ca3:/# apt-get install apache2</blockquote>


Type CTRL+P then CTRL+Q : this will exit the shell without killing the process
Now in the local machine, check out the container name


<blockquote>docker ps</blockquote>


Save the container with its apache installed (suppose your container name is happy_pasteur)


<blockquote>docker commit -a "witr " -m "install apache2" happy_pasteur witr/myapache</blockquote>


Stop the container


<blockquote>docker stop happy_pasteur</blockquote>


Start apache in new container "myapache" and bind ports


<blockquote>docker run -d -p 9999:80 witr/myapache /usr/sbin/apache2ctl -D FOREGROUND</blockquote>


Finally browse http://localhost:9999

