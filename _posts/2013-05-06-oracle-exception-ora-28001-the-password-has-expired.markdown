---
author: admin
comments: false
date: 2013-05-06 07:18:00+00:00
layout: post
link: https://witr.net/quotation/?p=65
slug: oracle-exception-ora-28001-the-password-has-expired
title: 'oracle: exception : Ora-28001: the password has expired'
wordpress_id: 65
categories:
- exception
- oracle
---

May 6, 2013  
  
  
this error tell us that user password has expired. check this with following request:  
SELECT USERNAME, PROFILE, ACCOUNT_STATUS, EXPIRY_DATE FROM dba_users WHERE username='your_oracle_username';  
value of ACCOUNT_STATUS column (expired or expired&locked;)  
  
password policies are defined in oracle PROFILE associated to user (value of PROFILE column). profile properties can be found here:  
select * from dba_profiles where profile = 'profile_name';  
  
take a look of line : resource_name ='PASSWORD_LIFE_TIME' and depending on your security policies you can change the value to UNLIMITED to avoid password expiry  
  


