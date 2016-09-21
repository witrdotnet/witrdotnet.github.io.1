---
author: admin
comments: false
date: 2015-07-23 12:51:05+00:00
layout: post
link: https://witr.net/quotation/?p=887
slug: migrate-local-docker-images-to-a-remote-docker-host
title: migrate local docker images to a remote docker host
wordpress_id: 887
categories:
- docker
---


**A. New remote host**
- install docker
- setup simple configuration to let docker daemon be accessible from other machines:
Edit /etc/default/docker, and add following line


<blockquote>
DOCKER_OPTS="-H tcp://0.0.0.0:2375"
</blockquote>


- restart docker daemon


<blockquote>
sudo service docker restart
</blockquote>


IMPORTANT:
With systemd systems (trusty and vivid), we must add new file : 
   /etc/systemd/system/docker.service.d/docker.conf
with following content:


<blockquote>
[Service]
EnvironmentFile=-/etc/default/docker
ExecStart=
ExecStart=/usr/bin/docker -d $DOCKER_OPTS
</blockquote>


And then restart socker.

Now, when trying :


<blockquote>
docker ps
</blockquote>


we'll got error:


<blockquote>
Get http:///var/run/docker.sock/v1.19/containers/json: dial unix /var/run/docker.sock: no such file or directory. Are you trying to connect to a TLS-enabled daemon without TLS?
</blockquote>


That's because docker client try to connect to file socket by default. So, from now, we must specify which host to connect to when running docker client. Like so :


<blockquote>
docker -H localhost:2375 ps
# or
docker -H 127.0.0.1:2375 ps
# or
simply docker -H :2375 ps
</blockquote>


Ok, but it's annoying to specify the host all the time !
So, the solution is to define an environment variable DOCKER_HOST:


<blockquote>
export DOCKER_HOST=0.0.0.0:2375
</blockquote>


then we can just run :


<blockquote>
docker ps
</blockquote>



**B. Local host**

We must set environment variable DOCKER_HOST like following (assume host machien ip is 192.168.33.10)


<blockquote>
export DOCKER_HOST=192.168.33.10:2375
</blockquote>



**C. transfer images from local docker host to remote docker host**
Now, to move all local images to the new docker host, we have to make it in three steps :
1. under local machine: export images as tar files


<blockquote>
docker -H "" save -o /tmp/myimage.tar myimage
</blockquote>


2. transfer tar files from local machine to the remote one (with scp for example)


<blockquote>
scp /tmp/myimage.tar user@192.168.33.10:/tmp/
</blockquote>


3. under remote machine: load images


<blockquote>
docker load -i /tmp/myimage.tar
</blockquote>


Hope this help

