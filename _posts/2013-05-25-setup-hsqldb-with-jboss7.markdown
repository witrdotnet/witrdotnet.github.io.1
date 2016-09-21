---
author: admin
comments: false
date: 2013-05-25 08:02:04+00:00
layout: post
link: https://witr.net/quotation/?p=659
slug: setup-hsqldb-with-jboss7
title: setup hsqldb with jboss7
wordpress_id: 659
categories:
- hsqldb
- jboss
---


jboss7 comes with h2 already installed and setup.
For hsqldb, just take h2 setup as example.

Following steps helps to setup hsqldb with jboss7.

**A. create new jboss7 module: hsqldb module**

1. first create directory $JBOSS_HOME/modules/org/hsqldb/main

    
    
    cd $JBOSS_HOME
    mkdir -p modules/org/hsqldb/main
    


2. download hsqldb and put the hsqldb.jar into created directory main
3. create into main directory following module.xml file (assuming hsqldb jar is hsqldb-x.x.x.jar)

    
    
    
    <module xmlns="urn:jboss:module:1.0" name="org.hsqldb">
      <resources>
        <resource-root path="hsqldb-x.x.x.jar"></resource-root>
      </resources>
       <dependencies>
         <module name="javax.api"></module>
         <module name="javax.transaction.api"></module>
       </dependencies>
    </module>
    



**B. setup hsqldb datasource**

1. add hsql driver by editing $JBOSS_HOME/standalone/configuration/standalone.xml (locate drivers in standalone.xml file)

    
    
    <drivers>  
      <driver name="hsqldb" module="org.hsqldb"></driver>  
      ...  
    </drivers>
    


2. finally add hsqldb datasource in $JBOSS_HOME/standalone/configuration/standalone.xml (locate datasources in the file)
we consider a file hsqldb database created into /home/hsqldb/data/witrHsqldb

    
    
    <datasource use-ccm="true" enabled="true" jndi-name="java:/jboss/datasources/witrHsqldb" use-java-context="true" jta="true" pool-name="witrHsqldb">  
      <connection-url>  
        jdbc:hsqldb:file:/home/hsqldb/data/witrHsqldb
      </connection-url>  
      <driver>  
        hsqldb  
      </driver>  
      <pool>  
        <prefill>false</prefill>  
        <use-strict-min>false</use-strict-min>  
        <flush-strategy>FailingConnectionOnly</flush-strategy>  
      </pool>  
      <security>  
        <user-name>  
          sa  
        </user-name>  
        <password>  
        </password>  
      </security>  
    </datasource>
    



