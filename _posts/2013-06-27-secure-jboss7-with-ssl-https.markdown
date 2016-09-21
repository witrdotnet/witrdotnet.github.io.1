---
author: admin
comments: false
date: 2013-06-27 08:11:00+00:00
layout: post
link: https://witr.net/quotation/?p=45
slug: secure-jboss7-with-ssl-https
title: secure jboss7 with ssl (https)
wordpress_id: 45
categories:
- https
- jboss
- ssl
---


  
  
1. create keystore certificate for jboss user  
> keytool -genkey -alias jboss -keyalg RSA  
  
2. edit jboss configuration file standalone.xml:  
- in interfaces : add new interface "local"

    
    
        <interfaces>
           ......
            <interface name="local">
                <inet-address value="127.0.0.1"></inet-address>
            </interface>
            ......
        </interfaces>
    




- in socket binding : add new socket binding "httpLocal" listening on localhost with http



    
    
        <socket-binding-group default-interface="public" port-offset="${jboss.socket.binding.port-offset:0}" name="standard-sockets">
           ......
            <socket-binding interface="local" name="httpLocal" port="8080"></socket-binding>
           ......
        </socket-binding-group>
    




  



  
- remove http connector :  
<strike><connector name="http" protocol="HTTP/1.1" scheme="http" socket-binding="http"/></strike>  
  

  


- add local http connector (for modules having to communicate in http with each others)


  
<connector name="http" protocol="HTTP/1.1" scheme="http" socket-binding="httpLocal"/>  
  
- add new https connector  
  
            <connector name="https" protocol="HTTP/1.1" scheme="https" socket-binding="https" secure="true">  
              <ssl password="password typed in step 1" />  
            </connector>  


  





in subsystem web we must finally have :



    
    
            <subsystem default-virtual-server="default-host" xmlns="urn:jboss:domain:web:1.1" native="false">
                <connector socket-binding="httpLocal" scheme="http" protocol="HTTP/1.1" name="http"></connector>
                <connector socket-binding="https" scheme="https" protocol="HTTP/1.1" name="https" secure="true">
                  <ssl password="pwd typed in step 1"></ssl>
                </connector>
                <virtual-server enable-welcome-root="true" name="default-host">
                    <alias name="localhost"></alias>
                    <alias name="example.com"></alias>
                </virtual-server>
            </subsystem>
    



