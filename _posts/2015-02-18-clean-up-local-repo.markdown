---
author: admin
comments: false
date: 2015-02-18 16:01:18+00:00
layout: post
link: https://witr.net/quotation/?p=706
slug: clean-up-local-repo
title: clean up local repo
wordpress_id: 706
categories:
- git
---


delete branches already deleted in remote repo


<blockquote>
witr$ git remote prune origin
</blockquote>


list local branches and theirs on remote : helps to see which local branch references to deleted remote branch


<blockquote>
witr$ git branch -vv
</blockquote>


delete branch referencing to deleted remote branch


<blockquote>
witr$ git branch -d branch-to-delete
</blockquote>


local clean up


<blockquote>
witr$ git clean -dfx
</blockquote>



