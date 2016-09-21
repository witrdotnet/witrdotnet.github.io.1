---
author: admin
comments: false
date: 2015-05-16 11:32:44+00:00
layout: post
link: https://witr.net/quotation/?p=824
slug: known-trouble-when-using-aapt
title: known trouble when using aapt
wordpress_id: 824
categories:
- android
---


You have trouble using aapt. And following error is raised : java.io.IOException: Cannot run program "/opt/Android/Sdk/build-tools/22.0.1/aapt": error=2, No such file or directory.
You are probably using aapt which is a 32bit application under a 64bit running ubuntu.
To get it working, simply install :


<blockquote>
sudo apt-get install lib32stdc++6 lib32z1
</blockquote>



