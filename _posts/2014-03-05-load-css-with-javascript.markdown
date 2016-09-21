---
author: admin
comments: false
date: 2014-03-05 10:38:31+00:00
layout: post
link: https://witr.net/quotation/?p=439
slug: load-css-with-javascript
title: load css with javascript
wordpress_id: 439
categories:
- css
- javascript
---



Following javascript function loads css file if it's not already loaded


    
    
    function loadIfNotYetLoaded(cssFilePathName){
    	cssLoaded = false;
    	var ss = document.styleSheets;
    	for (var i = 0, max = ss.length; i < max; i++) {
    		var sheet = ss[i];
    		if(sheet.href.indexOf(cssFilePathName) != -1){
    			cssLoaded = true;
    			break;
    		}
    	}
    
    	if(!cssLoaded){		
    		var link = document.createElement("link");
    		link.rel = "stylesheet";      
    		link.href = cssFilePathName;
    		document.getElementsByTagName("head")[0].appendChild(link);		
    	}
    }
    



