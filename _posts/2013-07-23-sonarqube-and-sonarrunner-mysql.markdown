---
author: admin
comments: false
date: 2013-07-23 14:59:00+00:00
layout: post
link: https://witr.net/quotation/?p=30
slug: sonarqube-and-sonarrunner-mysql
title: sonarQube and sonarRunner + mysql
wordpress_id: 30
categories:
- java
- mysql
- sonar
---

Analyse sonarQube standalone server :  


  





[MYSQL]




First of all prepare your mysql user sonar :




<blockquote>> mysql -uroot -p</blockquote>




<blockquote>    > use mysql;
> 
> 

> 
>     > create user sonar identified by 'sonar';
> 
> 

> 
>     > update user set host='%' where user = 'sonar';
> 
> 

> 
>     > create database sonar;
> 
> 

> 
>     > grant all privileges on sonar.* to sonar;
> 
> 

> 
>     > flush privileges;
> 
> 

> 
>     > quit
> 
> </blockquote>




  





[SOANR QUBE]  


- download sonar-x.x.x.zip




- unzip sonar-x.x.x.zip : 




<blockquote>> unzip sonar-x.x.x.zip -d /path/where/to/extract/ </blockquote>




- declare 




- edit /extracted/sonar/path/**conf/sonar.properties**








       1. comment     : sonar.jdbc.url:                            jdbc:h2:tcp://localhost:9092/sonar




       2. uncomment : sonar.jdbc.url:                            jdbc:mysql://127.0.0.1:3306/sonar[...]




- start sonar server : > /extracted/sonar/path/**bin//sonar.sh start**





- go to [http://localhost:9000](http://localhost:9000/)





  





[SONAR RUNNER]




- download sonar-runner-dist-x.x.x.zip




- unzip sonar-runner-dist-x.x.x.zip : 




<blockquote>> unzip sonar-runner-dist-x.x.x.zip -d /path/where/to/extract/ </blockquote>




- add environment variable SONAR_RUNNER_HOME: (ubuntu) edit /etc/environment and add SONAR_RUNNER_HOME=/sonar-runner/home/path/ 




- add $SONAR_RUNNER_HOME/bin to PATH : (ubuntu) edit /etc/environment and edit PATH




- go to your project home directory




- create file sonar-project.properties




- copy following in sonar-projetc.properties 

<blockquote># required metadata  
sonar.projectKey=witr:project  
sonar.projectName=proj  
sonar.projectVersion=1.0  
  
# optional description  
sonar.projectDescription=Fake description  
  
# path to source directories (required)  
sonar.sources=src/main  
  
# The value of the property must be the key of the language.  
sonar.language=java  
  
# Encoding of the source code  
sonar.sourceEncoding=UTF-8  
  
# Additional parameters  
#sonar.my.property=value  
</blockquote>







- finally analyse your project : 




<blockquote>> sonar-runner </blockquote>



