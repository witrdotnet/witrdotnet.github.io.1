---
author: admin
comments: false
date: 2013-12-09 10:28:00+00:00
layout: post
link: https://witr.net/quotation/?p=690
slug: nexus-exception-cannot-construct-org-codehaus-plexus-util-xml-xpp3dom-as-it-does-not-have-a-no-args-constructor
title: 'nexus exception : Cannot construct org.codehaus.plexus.util.xml.Xpp3Dom as
  it does not have a no-args constructor'
wordpress_id: 690
categories:
- exception
- sonatype nexus
- tomcat
---

Sonatype Nexus deployed on tomcat 6. At starting catalina raises following exception ($TOMCAT_HOME/log/catalina.out) 

<blockquote>2013-12-09 09:36:09 WARN  - o.c.p.PlexusContain~          - Error starting: class org.sonatype.nexus.DefaultNexus  
org.codehaus.plexus.personality.plexus.lifecycle.phase.StartingException: Could not start Nexus!  
        at org.sonatype.nexus.DefaultNexus.start(DefaultNexus.java:663)  
        at org.codehaus.plexus.PlexusLifecycleManager.start(PlexusLifecycleManager.java:303)  
        at org.codehaus.plexus.PlexusLifecycleManager.manageLifecycle(PlexusLifecycleManager.java:254)  
        at org.codehaus.plexus.PlexusLifecycleManager.manage(PlexusLifecycleManager.java:154)  
        at org.sonatype.guice.plexus.binders.PlexusBeanBinder.afterInjection(PlexusBeanBinder.java:78)  
  
[...]  
  
Caused by: com.thoughtworks.xstream.converters.ConversionException: Cannot construct org.codehaus.plexus.util.xml.Xpp3Dom as it does not have a no-args constructor : Cannot construct org.codehaus.plexus.util.xml.Xpp3Dom as it does not have a no-args constructor  
---- Debugging information ----  
message             : Cannot construct org.codehaus.plexus.util.xml.Xpp3Dom as it does not have a no-args constructor  
cause-exception     : com.thoughtworks.xstream.converters.reflection.ObjectAccessException  
cause-message       : Cannot construct org.codehaus.plexus.util.xml.Xpp3Dom as it does not have a no-args constructor  
class               : org.sonatype.nexus.configuration.model.CRepository  
required-type       : org.codehaus.plexus.util.xml.Xpp3Dom  
path                : /org.sonatype.nexus.configuration.model.CRepository/externalConfiguration  
line number         : 23  
------------------------------- </blockquote>

It happens because the version of nexus is not working correctly with java7. Must use java6 alternative.  
Edit $TOMCAT_HOME/bin/setclasspath.sh  
and add at the begining simple export env variable JAVA_HOME locating java6 home.
