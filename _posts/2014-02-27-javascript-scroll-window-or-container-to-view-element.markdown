---
author: admin
comments: false
date: 2014-02-27 08:54:31+00:00
layout: post
link: https://witr.net/quotation/?p=423
slug: javascript-scroll-window-or-container-to-view-element
title: 'javascript : scroll window or container to view element'
wordpress_id: 423
categories:
- javascript
---


prototypsjs framework is used for that.

- scroll container to view element inside : scrollTo(myElement, divContainer);
- scroll window to view element inside : scrollTo(myElement, null);

    
    
    scrollTo(myElement, scrollContainer){
        if(scrollContainer){
            myElement.scrollIntoView();
        }else{
            currentWindowScrollY = document.documentElement.scrollTop;
            targetWindowScrollY = Element.cumulativeOffset(myElement)[1]-window.height()+myElement.getHeight();
            if(targetWindowScrollY>currentWindowScrollY){
                window.scrollTo(window.scrollX, targetWindowScrollY);
            }
        }
    }
    



