---
author: admin
comments: false
date: 2014-03-20 15:01:35+00:00
layout: post
link: https://witr.net/quotation/?p=467
slug: jboss7-useful-jboss-cli-commands
title: 'Jboss7 : useful jboss-cli commands'
wordpress_id: 467
categories:
- jboss
---


jboss7 offer jboss-cli (command line interface) which makes live easier for administrators.

First of all connect to jboss-cli as following

**connect to jboss-cli : connect**

    
    
    [witr@WITR-PC]#cd $JBOSS_HOME
    [witr@WITR-PC]#./bin/jboss-cli.sh
    You are disconnected at the moment. Type 'connect' to connect to the server or 'help' for the list of supported commands.
    [disconnected /] connect
    [standalone@localhost:9991 /]
    



Then, here some useful jboss-cli commands

**undeploy and redeploy artifacts : deploy/undeploy**

    
    
    [standalone@localhost:9991 /] undeploy witr-4.2.15.war
    [standalone@localhost:9991 /] deploy standalone/deployments/witr-4.2.15.war
    



**list already deployed artifacts : deploy -l**

    
    
    [standalone@localhost:9991 /] deploy -l
    NAME                          RUNTIME-NAME                  ENABLED STATUS 
    wReport-4.0.13.war            wReport-4.0.13.war            true    OK     
    witr-4.2.15.war               witr-4.2.15.war               true    OK     
    witr-ws-4.0.1.jar             witr-ws-4.0.1.jar             true    OK     
    [standalone@localhost:9991 /] 
    



**handle log levels : /subsystem=logging**

Add new log level "INFO" on class net.witr.home.Himmel

    
    
    [standalone@localhost:9991 /] /subsystem=logging/logger=net.witr.home.Himmel:add(level=INFO)
    {"outcome" => "success"}
    [standalone@localhost:9991 /] 
    



Change log level of class net.witr.home.Himmel to "DEBUG"

    
    
    [standalone@localhost:9991 /] /subsystem=logging/logger=net.witr.home.Himmel:change-log-level(level=DEBUG)
    {"outcome" => "success"}
    [standalone@localhost:9991 /] 
    



Remove log level of class net.witr.home.Himmel

    
    
    [standalone@localhost:9991 /] /subsystem=logging/logger=net.witr.home.Himmel:remove
    {"outcome" => "success"}
    [standalone@localhost:9991 /] 
    



**handle system properties : /system-property**
Add, read and remove system property witrActive

    
    
    [standalone@localhost:9991 /] /system-property=witrActive:add(value=Y)
    {"outcome" => "success"}
    [standalone@localhost:9991 /] /system-property=witrActive:read-resource
    {
        "outcome" => "success",
        "result" => {"value" => "Y"}
    }
    [standalone@localhost:9991 /] /system-property=witrActive:remove
    {"outcome" => "success"}
    




