---
author: admin
comments: false
date: 2014-07-02 10:02:58+00:00
layout: post
link: https://witr.net/quotation/?p=534
slug: browse-sdcard-of-your-avd-android-virtual-device
title: browse sdcard of your avd (Android Virtual Device)
wordpress_id: 534
categories:
- android
---


you have already installed android studio or android sdk.

type


<blockquote>
> cd $ANDROID_SDK_HOME
> ./tools/ddms
</blockquote>



If your avd is started you will see it in ddms Monitor (else go [here](http://quote.witr.net/?p=532) to see how starting avd).

Select your avd and then go to menu Device->File Explorer

