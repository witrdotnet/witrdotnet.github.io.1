---
author: admin
comments: false
date: 2014-03-14 13:41:13+00:00
layout: post
link: https://witr.net/quotation/?p=456
slug: xslt-java-debug
title: XSLT java debug
wordpress_id: 456
categories:
- java
- xsl
---


You may need some debug message to be logged in standard output

java debug class

    
    
    package net.witr.xslt;
    
    public class XslDebug {
    
        public static void debug(String msg){
            System.out.println(msg);
        }
    
    }
    


xsl code

    
    
    <xsl:stylesheet xmlns:witrdebug="net.witr.xslt.XslDebug">
      ..
      <xsl:template match="DIV">
        <xsl:variable name="debugName" select="name(.)"></xsl:variable>
        <xsl:variable name="debugStyle" select="@style"></xsl:variable>
        <xsl:value-of select="witrDebug:debug(concat('Matched ',$debugName,'; style :',$debugStyle))"></xsl:value-of>
      </xsl:template>
      ..
    </xsl:stylesheet>
    




