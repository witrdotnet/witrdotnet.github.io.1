---
author: admin
comments: false
date: 2014-07-02 09:42:40+00:00
layout: post
link: https://witr.net/quotation/?p=532
slug: play-your-apk-file-on-android-emulator
title: play your apk file on android emulator
wordpress_id: 532
categories:
- android
---


you have already installed android studio or android sdk.
you have already configure your avd (android virtual device)

**1. list your AVDs**


<blockquote>
> cd $ANDROID_SDK_HOME
> ./tools/android list avds
</blockquote>



result looks like


<blockquote>
Available Android Virtual Devices:
    Name: AVD_for_Nexus_S_by_Google
    Path: /home/witr/.android/avd/AVD_for_Nexus_S_by_Google.avd
  Target: Android 4.2.2 (API level 17)
     ABI: armeabi-v7a
    Skin: 480x800
---------
    Name: AVD_for_Galaxy_Nexus_by_Google
    Path: /home/witr/.android/avd/AVD_for_Galaxy_Nexus_by_Google.avd
  Target: Android 4.2.2 (API level 17)
     ABI: armeabi-v7a                                                                                                                                                                                                                                                 
    Skin: 720x1280 
</blockquote>



**2. start emulator of @AVD_for_Galaxy_Nexus_by_Google**


<blockquote>
> ./tools/emulator @AVD_for_Galaxy_Nexus_by_Google
</blockquote>


or


<blockquote>
> ./tools/android avd
</blockquote>


Then select your avd and click start

**3. install your apk file**
copy your apk file (e.g. myApplication.apk) in $ANDROID_SDK_HOME/platform-tools/
Once avd started, open new terminal and type


<blockquote>
> cd $ANDROID_SDK_HOME/platform-tools
> ./adb install myApplication.apk
</blockquote>


If install succeed you will have


<blockquote>
* daemon not running. starting it now on port 5037 *
* daemon started successfully *
2594 KB/s (326422 bytes in 0.122s)
        pkg: /data/local/tmp/myApplication.apk
Success
</blockquote>


 
**4. launch your application in avd**
go to your avd emulator and launch myApplication


