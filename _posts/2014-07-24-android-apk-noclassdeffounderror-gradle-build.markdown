---
author: admin
comments: false
date: 2014-07-24 14:45:12+00:00
layout: post
link: https://witr.net/quotation/?p=591
slug: android-apk-noclassdeffounderror-gradle-build
title: android apk NoClassDefFoundError (gradle build)
wordpress_id: 591
categories:
- android
- java
---


My android application is build with gradle and my apk is generated and works correctly.
After some developpement iterations, i include android-support-v4.jar library to ide project and gradle build file like following:

    
    
    compile files('libs/android-support-v4.jar')
    



Build with gradle and install apk on avd ==> NoClassDefFoundError (class which extends class located in android-support-v4.jar library)

Solution:


<blockquote>
./gradlew clean
</blockquote>



And it works again

