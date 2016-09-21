---
author: admin
comments: false
date: 2014-04-17 09:57:03+00:00
layout: post
link: https://witr.net/quotation/?p=479
slug: jboss7-jboss-cli-how-to-redirect-specified-class-log-in-specified-file
title: 'Jboss7 (jboss-cli) : how to redirect specified class log in specified file'
wordpress_id: 479
categories:
- jboss
---


Don't edit standalone.xml and then restart jboss, just use jboss-cli commands. Only three steps are enough

**1. Add a file log handler**


<blockquote>
/subsystem=logging/file-handler=**HANDLER_NAME**:add(file={"path"=>"**FILE_NAME**","relative-to"=>"jboss.server.log.dir"},level="**LEVEL**")

> 
> </blockquote>


**2. Add a log category**


<blockquote>
/subsystem=logging/logger=**CATEGORY_NAME**:add(level="**LEVEL**")

> 
> </blockquote>


**3. Add a log handlers to a log category**


<blockquote>
/subsystem=logging/logger=**CATEGORY_NAME**:assign-handler(name="**HANDLER_NAME**")

> 
> </blockquote>



done...

**By example :** We have to redirect net.witr.MyClass info logs to witr.log file

    
    
    [witr@WITR-PC]#cd $JBOSS_HOME
    [witr@WITR-PC]#./bin/jboss-cli.sh
    You are disconnected at the moment. Type 'connect' to connect to the server or 'help' for the list of supported commands.
    [disconnected /] connect
    [standalone@localhost:9991 /] /subsystem=logging/file-handler=WITR_HANDLER:add(file={"path"=>"witr.log","relative-to"=>"jboss.server.log.dir"},level="INFO")
    [standalone@localhost:9991 /] /subsystem=logging/logger=net.witr.MyClass:add(level="INFO")
    [standalone@localhost:9991 /] /subsystem=logging/logger=net.witr.MyClass:assign-handler(name="WITR_HANDLER")
    




