---
author: admin
comments: false
date: 2013-03-22 08:30:00+00:00
layout: post
link: https://witr.net/quotation/?p=80
slug: graphml-de-ton-projet-java
title: graphml de ton projet java
wordpress_id: 80
categories:
- java
---

March 22, 2013  
  
  
utils:  
- degraph (https://github.com/schauder/degraph) / download: http://schauder.github.com/degraph//download/degraph-0.0.3.zip  
- yEd (http://www.yworks.com/en/downloads.html#yEd) / download: http://www.yworks.com/en/products_download.php?file=yEd-3.10.2.zip  
  
howto:  
1. download degraph-0.0.3.zip and yEd-3.10.2.zip  
2. unzip them in corresponding directories: degraph-0.0.3, yEd-3.10.2  
3. > ./degraph-0.0.3/bin/degraph -c path/to/my_jar.jar -o /tmp/output.graphml -i witr.**  
    this command line will scan only witr.** classes of your my_jar.jar and create output.graphml file  
4. > cd yEd-3.10.2  
    > java -jar yEd-3.10.2/yed.jar  
    this wll run yEd. be sure that you can connect to X11 window server  
5. use yEd gui to open output.graphml file  
6. if the graph is not well presented then menu: layout>organic>  
    preferred edge length = 117  
    minimal node distance = 50  
    avoid node/edge overlaps : check  
    compacteness = 0.9  
    ===> validate by pressing ok  
  
enjoy
