---
author: admin
comments: false
date: 2013-12-05 15:01:00+00:00
layout: post
link: https://witr.net/quotation/?p=683
slug: interactive-ruby-simplify-your-computing
title: 'Interactive Ruby : simplify your computing'
wordpress_id: 683
categories:
- ruby
- tricks
---

Interactive Ruby helps you to make complex computations without having to write a whole program.  
Under linux type irb.  
  
Ex1. calculate (10-7+500)*(4 power 3 )-square root of(900) 

<blockquote>irb(main):001:0> (10-7+500)*(4**3)-Math.sqrt(900)  
=> 32162.0 </blockquote>


  
Ex2. get exact date at 14 days before now (in seconds 14x24x60x60 before now) 

<blockquote>irb(main):002:0> Time.new - (14*24*60*60)  
=> Thu Nov 21 15:52:53 +0100 2013 </blockquote>



