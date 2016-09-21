---
author: admin
comments: false
date: 2013-07-18 13:29:00+00:00
layout: post
link: https://witr.net/quotation/?p=37
slug: main-class-in-manifest-with-maven
title: main class in manifest with maven
wordpress_id: 37
categories:
- java
- maven
---

to declare your main class in the manifest file of your projet with maven. In pom add following (bold):

    
    
    <build>
        <sourcedirectory>src</sourcedirectory>
        <plugins>
           <plugin>
              <groupid>org.apache.maven.plugins</groupid>
              <artifactid>maven-jar-plugin</artifactid>
              <configuration>
                 <archive>
                    <manifest>
                       <addclasspath>true</addclasspath>
                       <mainclass>net.witr.Application</mainclass>
                    </manifest>
                 </archive>
              </configuration>
           </plugin>
        </plugins>
    </build>
    



