---
author: admin
comments: false
date: 2011-09-20 07:31:00+00:00
layout: post
link: https://witr.net/quotation/?p=100
slug: highlight-results-with-javascript
title: highlight results with javascript
wordpress_id: 100
categories:
- javascript
---

September 20, 2011  
  
highlight results with javascript (prototype required)  
  
function highlightWordSearching(componentId, search){  
    if(search && !search.blank()){  
     search = search.replace('&','&');  
        var search_regexp = new RegExp('>([^<]*)?('+search.trim()+')([^>]*)?<','ig');  
        $(componentId).innerHTML = $(componentId).innerHTML.replace(search_regexp,'>$1$2$3<');  
    }  
}  


  




