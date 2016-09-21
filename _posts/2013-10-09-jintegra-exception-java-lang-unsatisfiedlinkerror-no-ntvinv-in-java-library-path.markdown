---
author: admin
comments: false
date: 2013-10-09 13:07:00+00:00
layout: post
link: https://witr.net/quotation/?p=19
slug: jintegra-exception-java-lang-unsatisfiedlinkerror-no-ntvinv-in-java-library-path
title: 'Jintegra exception : java.lang.UnsatisfiedLinkError: no ntvinv in java.library.path'
wordpress_id: 19
categories:
- exception
- java
---

running java project using jintegra to handling word documents.  
  
having following exception: **java.lang.UnsatisfiedLinkError: no ntvinv in java.library.path **means that the dll library doesn't exist in one of paths listed in java.library.path system property.  
  
Fix:  
add java argument :  -Djava.library.path=/path/to/dir/of/dll
