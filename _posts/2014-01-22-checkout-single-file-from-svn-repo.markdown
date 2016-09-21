---
author: admin
comments: false
date: 2014-01-22 13:58:01+00:00
layout: post
link: https://witr.net/quotation/?p=411
slug: checkout-single-file-from-svn-repo
title: checkout single file from svn repo
wordpress_id: 411
categories:
- svn
---


svn co doesn't permit checkout files but directories.
use rather :


<blockquote>svn export https://svn.repo/path/to/file/witr.png /tmp/witr.png</blockquote>


another alternative for text files


<blockquote>svn cat https://svn.repo/path/to/file/witr.txt > /tmp/witr.txt</blockquote>



