---
author: admin
comments: false
date: 2014-01-07 17:57:38+00:00
layout: post
link: https://witr.net/quotation/?p=692
slug: hbm2java-with-ant-step-by-step
title: hbm2java with ant step by step
wordpress_id: 692
categories:
- ant
- hibernate
- java
---


- workspace structure:
+ hbm/
+ build.xml
+ hibernate.cfg.xml
+ reveng.xml
+ lib/

- build.xml

    
    
    <project basedir="." name="hbm">
    
    <path id="toolslib">
     <path location="lib/hibernate-tools-3.4.0.CR2.jar"></path>
    
     <path location="lib/freemarker.jar"></path>
     <path location="lib/ojdbc14-10.2.0.1.0.jar"></path>
     <path location="lib/commons-logging-1.0.4.jar"></path>
     <path location="lib/dom4j-1.6.1.jar"></path>
     <path location="lib/slf4j-api-1.6.1.jar"></path>
     <path location="/home/jboss/.m2/repository/org/hibernate/hibernate-core/3.5.4-Final/hibernate-core-3.5.4-Final.jar"></path>
     <path location="/home/jboss/.m2/repository/org/hibernate/hibernate-validator-legacy/4.0.2.GA/hibernate-validator-legacy-4.0.2.GA.jar"></path>
     <path location="/home/jboss/.m2/repository/org/hibernate/hibernate-entitymanager/3.5.5-Final/hibernate-entitymanager-3.5.5-Final.jar"></path>
     <path location="/home/jboss/.m2/repository/org/hibernate/hibernate-envers/3.5.4-Final/hibernate-envers-3.5.4-Final.jar"></path>
     <path location="/home/jboss/.m2/repository/org/hibernate/hibernate-jpamodelgen/1.0.0.Final/hibernate-jpamodelgen-1.0.0.Final.jar"></path>
     
     <path location="/home/jboss/.m2/repository/org/hibernate/javax/persistence/hibernate-jpa-2.0-api/1.0.0.Final/hibernate-jpa-2.0-api-1.0.0.Final.jar"></path>
     <path location="/home/jboss/.m2/repository/org/hibernate/hibernate-validator/4.0.2.GA/hibernate-validator-4.0.2.GA.jar"></path>
     <path location="/home/jboss/.m2/repository/org/hibernate/hibernate-commons-annotations/3.2.0.Final/hibernate-commons-annotations-3.2.0.Final.jar"></path>
     <path location="/home/jboss/.m2/repository/org/hibernate/hibernate-annotations/3.5.5-Final/hibernate-annotations-3.5.5-Final.jar"></path>
     <path location="/home/jboss/.m2/repository/com/ginerativ/envers/hibernate-envers/1.1.0.GA.ginerativ/hibernate-envers-1.1.0.GA.ginerativ.jar"></path>
    
     <path location="/home/jboss/.m2/repository/cglib/cglib/2.2/cglib-2.2.jar"></path>
     <path location="/home/jboss/.m2/repository/asm/asm/3.1/asm-3.1.jar"></path>
     <path location="/home/jboss/.m2/repository/commons-collections/commons-collections/3.2.1/commons-collections-3.2.1.jar"></path>
    </path>
    
    <taskdef classname="org.hibernate.tool.ant.HibernateToolTask" classpathref="toolslib" name="hibernatetool"></taskdef>
    
    
    <hibernatetool destdir="generated">
     <classpath>
      <path location="classes"></path>
     </classpath>
    
     <jdbcconfiguration revengfile="reveng.xml" packagename="net.witr.hbm2java.demo" configurationfile="hibernate.cfg.xml"></jdbcconfiguration>
     <hbm2java ejb3="true"></hbm2java>
    </hibernatetool>
    
    </project>
    



- hibernate.cfg.xml

    
    
    
    
    <hibernate-configuration>
      <session-factory name="WitrSessionFactory">
            <property name="bytecode.use_reflection_optimizer">true</property>
            <property name="connection.driver_class">oracle.jdbc.driver.OracleDriver</property>
            <property name="connection.url">jdbc:oracle:thin:@127.0.0.1:1522:WITRDB</property>
            <property name="connection.username">witr</property>
            <property name="connection.password">witr</property>
            <property name="dialect">org.hibernate.dialect.Oracle10gDialect</property>
            <property name="show_sql">false</property>
     </session-factory>
    </hibernate-configuration>
    



- reveng.xml

    
    
    
    
    
    <hibernate-reverse-engineering>
    
            <type-mapping>
                    <sql-type jdbc-type="NUMERIC" not-null="true" hibernate-type="long"></sql-type>
                    <sql-type jdbc-type="NUMERIC" not-null="false" hibernate-type="java.lang.Long"></sql-type>
                    <sql-type jdbc-type="DECIMAL" not-null="true" hibernate-type="long"></sql-type>
                    <sql-type jdbc-type="DECIMAL" not-null="false" hibernate-type="java.lang.Long"></sql-type>
                    <sql-type jdbc-type="VARCHAR" length="1" not-null="false" hibernate-type="java.lang.Character"></sql-type>
                    <sql-type jdbc-type="VARCHAR" length="1" not-null="true" hibernate-type="char"></sql-type>
                    <sql-type jdbc-type="VARCHAR" hibernate-type="string"></sql-type>
            </type-mapping>
    
            <table-filter match-schema="WITRSCHEMA" match-name="WITR_TABLE1"></table-filter>
            <table-filter match-schema="WITRSCHEMA" match-name="WITR_TABLE2"></table-filter>
            <table-filter match-schema="WITRSCHEMA" match-name="WITR_TABLE3"></table-filter>
            ...etc
    
    </hibernate-reverse-engineering>
    



then type

    
    
    > cd hbm
    > ant
    



your hibernate beans are ready in hbm/generated directory

