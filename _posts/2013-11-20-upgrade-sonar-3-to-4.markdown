---
author: admin
comments: false
date: 2013-11-20 13:59:00+00:00
layout: post
link: https://witr.net/quotation/?p=684
slug: upgrade-sonar-3-to-4
title: upgrade sonar 3 to 4
wordpress_id: 684
categories:
- sonar
---

so easy as 5 simple steps :  
- Download and unzip new sonarqube-4.0.zip : > unzip sonarqube-4.0.zip -d $NEW_SONAR_HOME  
- Manually edit sonarqube-4.0/conf/sonar.properties and sonarqube-4.0/conf/wrapper.conf and copy old properties values from old sonar conf  
- Copy extensions from old sonar to the new one (only extensions not having correspondent in the new sonar)  
- stop old sonar and start the new one :  
> $OLD_SONAR_HOME/bin/yourOS/sonar.sh stop  
> $NEW_SONAR_HOME/bin/yourOS/sonar.sh start  
- Go to http://localhost:9000/setup (assuming sonar listen in localhost) and finally click under upgrade button  


  




