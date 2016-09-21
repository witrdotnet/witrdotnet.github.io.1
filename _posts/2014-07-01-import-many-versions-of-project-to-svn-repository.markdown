---
author: admin
comments: false
date: 2014-07-01 13:43:44+00:00
layout: post
link: https://witr.net/quotation/?p=523
slug: import-many-versions-of-project-to-svn-repository
title: import many versions of project to svn repository
wordpress_id: 523
categories:
- svn
---


I have traditionally versionning my project by copying my project folder, rename the copy and continue work on it.

Now, I have several versions of my project in different folders: myproj_v1, myproj_v2, ...
I want to import my project version by version. So, I'll have change log.

To import like so (e.g. to http://svn.witr.net/repos/myproj), we have to type following commands:
**1. copy first version in different folder**

    
    [witr@localhost] cp -r myproj_v1 myproj


**2. import to svn**

    
    [witr@localhost] svn import -m "first import v1" ./myproj http://svn.witr.net/repos/myproj


**3. rsync the second version**

    
    [witr@localhost] rsync -ah myproj_v2 myproj


**4. force add unversionned elements**

    
    
    [witr@localhost] cd myproj
    [witr@localhost] svn add --force * --auto-props --parents --depth infinity -q
    


**5. commit second version**

    
    [witr@localhost] svn ci -m "commit v2"



==> repeat steps 3, 4, 5 to continue with next versions folders

