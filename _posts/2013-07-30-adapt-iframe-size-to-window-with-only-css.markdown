---
author: admin
comments: false
date: 2013-07-30 13:54:00+00:00
layout: post
link: https://witr.net/quotation/?p=24
slug: adapt-iframe-size-to-window-with-only-css
title: adapt iframe size to window with only css
wordpress_id: 24
categories:
- css
---


css :  


    
    
    div#container {
        position: fixed;
        top: 0px;
        left: 0px;
        bottom: 0px;
        right: 0px;
    }
    div#container iframe {
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        height: 100%;
        width: 100%;
    }
    


html :  


    
    
    <div id="container">
        <iframe src="http://your_url"></iframe>
    </div>
    



