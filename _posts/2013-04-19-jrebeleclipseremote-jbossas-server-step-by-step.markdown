---
author: admin
comments: false
date: 2013-04-19 07:20:00+00:00
layout: post
link: https://witr.net/quotation/?p=67
slug: jrebeleclipseremote-jbossas-server-step-by-step
title: jrebel/eclipse/remote jbossAS server step by step
wordpress_id: 67
categories:
- jboss
---


  
April 19, 2013  
  
install jrebel with eclipse:  
- get licence from jrebel web site  
- install jrebel eclipse plugin. Restart eclipse and activate you licence  
- in jrebel config center : select one projet in projects panel, and enter in corresponding "deployment URL" field your jboss7 server url (example http://myserver:8080)  
   you will have "Server responded with an error: null", don't worry, this because server was not yet configured to respond to remote requests  
- now compile and package your project and then put it in your server jboss.  
  
install jrebel under jboss7  
- copy "C:UsersYOURHOME.jrebeljrebel.lic" et "C:UsersYOURHOME.jrebeljrebel.properties" to the home of your server user launching jboss : /home/user_launchig_jboss/.jrebel/  
- get jrebel.jar from jrebel web site and put it in your host machine  
- add following in the script launching jboss7 before call standalone.sh :  
export JAVA_OPTS="$JAVA_OPTS -javaagent:/path/to/jrebel.jar -Drebel.log.file=$JBOSS_HOME/standalone/log/jrebel.log -Drebel.remoting_plugin=true"  
- start server jboss7  
=============================  
if you have following error : Server responded with an error: null ==> this because remoting is not enabled in jrebel java agent : add  -Drebel.remoting_plugin=true in java_opts  
if you have following error : Server responded with an error: Remoting module'navco-module-delegal-postes-pm' was not found ==> redeploy your project in jboss7 (jrebel remoting needs the rebel-remote.xml)  


  




