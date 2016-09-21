---
author: admin
comments: false
date: 2013-07-18 13:24:00+00:00
layout: post
link: https://witr.net/quotation/?p=38
slug: include-all-files-with-maven-jar-plugin
title: include all files with maven-jar-plugin
wordpress_id: 38
categories:
- java
- maven
---

Context : pom which use maven-jar-plugin to package jar.  
in the source code ther were some non java files (gif, html, ...) which aren't included in produced jar file when executing maven install..  
  
Only compiled java classes are included, maven-jar-plugin filters resources by default: to disable filter we maust add following (bold gray):

    
    
    <build>
        <sourcedirectory>src</sourcedirectory>
        <resources>
           <resource>
              <directory>src</directory>
              <filtering>false</filtering>
           </resource>
        </resources>
        <plugins>
           <plugin>
              <groupid>org.apache.maven.plugins</groupid>
              <artifactid>maven-jar-plugin</artifactid>
           </plugin>
        </plugins>
    </build>
    



