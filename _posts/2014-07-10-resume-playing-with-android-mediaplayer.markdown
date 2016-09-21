---
author: admin
comments: false
date: 2014-07-10 16:26:56+00:00
layout: post
link: https://witr.net/quotation/?p=537
slug: resume-playing-with-android-mediaplayer
title: resume android MediaPlayer after pause
wordpress_id: 537
categories:
- android
- java
---


To pause MediaPlayer use : 

    
    
    mediaPlayer.pause();
    



And to resume

    
    
    int pausePosition = mediaPlayer.getCurrentPosition();
    mediaPlayer.seekTo(pausePosition);
    mediaPlayer.start();
    




