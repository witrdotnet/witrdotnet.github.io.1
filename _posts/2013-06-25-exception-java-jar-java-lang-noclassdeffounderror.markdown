---
author: admin
comments: false
date: 2013-06-25 10:32:00+00:00
layout: post
link: https://witr.net/quotation/?p=47
slug: exception-java-jar-java-lang-noclassdeffounderror
title: 'exception : "java -jar" java.lang.NoClassDefFoundError'
wordpress_id: 47
categories:
- java
---

when you execute a jar file with java, you have to know that in the jar file we must declare the main class and th classpath in the manifest file.  
  
extarct MANIFEST.MF  
> jar xvf myjar.jar META-INF/MANIFEST.MF  
see its content  
> vi META-INF/MANIFEST.MF  
it looks like :  
  
Manifest-Version: 1.0  
Ant-Version: Apache Ant 1.5.3  
Created-By: 1.4.2_02-b03 (Sun Microsystems Inc.)  
Main-Class: xxx.package.MainClassName  
Class-Path: ./lib/a.jar  ./lib/b.jar  
  
if you have NoClassDefFoundError when launching the jar, look for the missed jar library in the web, download it and put it in lib directory for example, and finally declare it in the manifest like others (./lib/a.jar ./lib/b.jar ./lib/c.jar). so :  
  
> mkdir unzippedjar  
> unzip myjar -d unzippedjar/  
> cd unzippedjar  
> vi META-INF/MANIFEST.MF  
edit the manifest file : add missed lib to classpath, and save  
> zip -r ../myjar.jar *  
  
re-execute your myjar.jar and it must work  
  
==========================  
case of delineate which miss xalan-2.7.1.jar as library.  
  

