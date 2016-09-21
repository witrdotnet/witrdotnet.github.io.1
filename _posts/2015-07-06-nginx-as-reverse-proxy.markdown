---
author: admin
comments: false
date: 2015-07-06 15:37:17+00:00
layout: post
link: https://witr.net/quotation/?p=883
slug: nginx-as-reverse-proxy
title: nginx as reverse proxy
wordpress_id: 883
categories:
- network
---


I'm working on dockerizing several projects with docker-compose. And, I automated checkout from git repository and building projects,
One of maven projects inherits from parent pom the url of nexus repository. And unfortunately, nexus server was moved to a new url. This fails maven build, because it can't download artifacts from old nexus url.

While I have no time to fix nexus url in parent pom and recompile all depending projects. And while I'm rushed to run and validate my docker-compose. I'm looking for rapid solution.

We can simply use hosts to redirect old url to the new one. But in my case, it's not possible because the old url contains a port number.

old_url: http://oldurl.net:8080
new url: https://newurl.net

So, I use nginx as reverse proxy to solve problem:

Step1: install nginx


<blockquote>
$ sudo apt-get install nginx
</blockquote>


Step2: nginx configuration
create /etc/nginx/conf.d/witr.conf with following content


<blockquote>
server {
    listen 8080;
    server_name oldurl.net;
    location / {
        proxy_pass https://newurl.net;
        proxy_redirect off;
    }
}
</blockquote>


Step3: locally redirect server name
edit /etc/hosts and add new entry


<blockquote>
127.0.0.1      oldurl.net
</blockquote>


Step4: restart nginx


<blockquote>
service nginx restart
</blockquote>


Finally : run my automated build. On download, maven will ask oldurl:8080. hosts will redirect to nginx. Nginx will redirect to newurl. And maven will be able to download artifacts and build will not fail.

