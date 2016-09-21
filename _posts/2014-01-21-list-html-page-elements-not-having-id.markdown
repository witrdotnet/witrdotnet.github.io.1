---
author: admin
comments: false
date: 2014-01-21 16:25:22+00:00
layout: post
link: https://witr.net/quotation/?p=699
slug: list-html-page-elements-not-having-id
title: list html page elements not having id
wordpress_id: 699
categories:
- icefaces
- javascript
---


Icefaces ajax render performances issues could be sequence of dom elements without id. The present post helps to list all elements not having id to be fixed.

Open your page in your browser.
In developer console create following function

    
    
    function chkid(ch){
      if(ch.id==""){
        console.log(ch.tagName+' : '+ch.id + ' childof ==> ' + ch.up().id)
      }
      ch.childElements().each(
        function(fils){
          chkid(fils)
        }
      );
    }
    


then call chkid with any dom element. To get all, call chkid with body element

    
    
    $$('body')[0].childElements().each(function(ch){chkid(ch)});
    



**Nota :** Here we use prototypejs framework

