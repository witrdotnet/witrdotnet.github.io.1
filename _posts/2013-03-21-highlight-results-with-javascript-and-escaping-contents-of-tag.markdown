---
author: admin
comments: false
date: 2013-03-21 08:30:00+00:00
layout: post
link: https://witr.net/quotation/?p=82
slug: highlight-results-with-javascript-and-escaping-contents-of-tag
title: highlight results with javascript and escaping contents of tag
wordpress_id: 82
categories:
- javascript
---

March 21, 2013  
  
  
substitute regexp by this one var search_regexp = new RegExp('(?!]*?>)>([^<]*)?('+search.trim()+')([^>]*)?(?![^<]*?)<','ig');  
  
function highlightWordSearching(componentId, search){  
    if(search && !search.blank()){  
     search = search.replace('&','&');  
        var search_regexp = new RegExp('>([^<]*)?('+search.trim()+')([^>]*)?<','ig');  
        $(componentId).innerHTML = $(componentId).innerHTML.replace(search_regexp,'>$1$2$3<');  
    }  
}  


  




