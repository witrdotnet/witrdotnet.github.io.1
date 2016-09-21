---
author: admin
comments: false
date: 2012-04-15 14:03:51+00:00
layout: post
link: https://witr.net/quotation/?p=463
slug: import-oracle-dump-file
title: import oracle dump file
wordpress_id: 463
categories:
- oracle
---


import dump file
>> imp witr/passwd@WITRDBIDENT file=/tmp/expdat.dmp fromuser=witr touser=witr log =/tmp/imp.log

import one table from dump file
>> imp witr/passwd@WITRDBIDENT file=/tmp/expdat.dmp fromuser=witr touser=witr tables=T_WITR log =/tmp/imp.log


