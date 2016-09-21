---
author: admin
comments: false
date: 2013-05-28 06:57:00+00:00
layout: post
link: https://witr.net/quotation/?p=58
slug: exception-service-entry-org-jboss-as-jsf-deployment-jsfinjectionprovider-does-not-extend
title: 'exception: Service entry ''org.jboss.as.jsf.deployment.JsfInjectionProvider''
  does not extend'
wordpress_id: 58
categories:
- exception
- jboss
- jsf
---


  
=========================================== 28/05/2013  
exception:  
Service entry 'org.jboss.as.jsf.deployment.JsfInjectionProvider' does not extend DiscoverableInjectionProvider  
==> solution add in web.xml  
      
        org.jboss.jbossfaces.WAR_BUNDLES_JSF_IMPL  
        true  
      


  




