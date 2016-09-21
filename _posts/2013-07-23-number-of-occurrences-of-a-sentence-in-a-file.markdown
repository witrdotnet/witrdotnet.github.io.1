---
author: admin
comments: false
date: 2013-07-23 15:17:00+00:00
layout: post
link: https://witr.net/quotation/?p=29
slug: number-of-occurrences-of-a-sentence-in-a-file
title: number of occurrences of a sentence in a file
wordpress_id: 29
categories:
- linux
---

<blockquote>awk -F "your sentence" '{s+=(NF-1)} END {print s}'  yourFile </blockquote>
