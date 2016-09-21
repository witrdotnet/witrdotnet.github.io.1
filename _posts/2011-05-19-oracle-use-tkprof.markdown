---
author: admin
comments: false
date: 2011-05-19 07:07:00+00:00
layout: post
link: https://witr.net/quotation/?p=101
slug: oracle-use-tkprof
title: 'oracle: use tkprof'
wordpress_id: 101
categories:
- oracle
---


  
================================================= 19/06/2011  
use tkprof  
1. Login with oracle user  
2. Sqlplus system/xxxx@SHEMA  
3. alter system set sql_trace=true;  
4. show parameter user_dump_dest;  
4. Cd   
5. tkprof xxxxx.trc /tmp/myAnalyse.out explain=user/pass@SHEMA sort=execpu  
6. ne pas oublier : alter system set sql_trace=false;  


  




