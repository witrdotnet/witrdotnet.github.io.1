---
author: admin
comments: false
date: 2014-06-24 16:24:33+00:00
layout: post
link: https://witr.net/quotation/?p=520
slug: profile-remote-host-jboss7-with-jprofiler
title: profile remote host jboss7 with jprofiler
wordpress_id: 520
categories:
- java
- jboss
- jprofiler
---



**local machine**
- create ssh tunnel : ssh -L 8849:127.0.0.1:8849 remoteuser@remotehost
- launch jprofiler : e.g. /mnt/jprofiler7/bin/jprofiler
- new session -> remote host -> enter host 127.0.0.1 as port 8849 -> save session (don't start session you must accomplish remote host configuration and restart server before)

**remote host (linux x64)**
- install(unzip) jprofiler in any folder in remote host file system : e.g. /opt/jprofiler
- edit $JBOSS_HOME/bin/standlaone.sh and add following (this will launch jprofiler agent uppon jboss server. jprofiler agent will listen on port 8849)

    
    
    export JAVA_OPTS="$JAVA_OPTS -agentpath:/opt/jprofiler/bin/linux-x64/libjprofilerti.so=port=8849"
    


- restart jboss server

**local machine**
- start jprofiler saved session

That's all

