---
author: admin
comments: false
date: 2013-07-19 15:23:00+00:00
layout: post
link: https://witr.net/quotation/?p=34
slug: maven-next-version
title: maven next version
wordpress_id: 34
categories:
- java
- maven
---

if you are curious and want to know how maven produce release version and next version you can try to debug its behavior by using following code:

    
    
    import org.apache.maven.shared.release.versions.DefaultVersionInfo;
    import org.apache.maven.shared.release.versions.VersionParseException;
    
    public static void main(String []args){
        try {
            String version = "1.2.3-SNAPSHOT";
            DefaultVersionInfo v = new DefaultVersionInfo(version);
            System.out.println("version         : " + version);
            System.out.println("release version : " + v.getReleaseVersionString());
            System.out.println("next verison    : " + v.getNextVersion());
        } catch (VersionParseException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
    }
    




don't forget to add maven-release-manager in classpath or in your project pom as dependency



