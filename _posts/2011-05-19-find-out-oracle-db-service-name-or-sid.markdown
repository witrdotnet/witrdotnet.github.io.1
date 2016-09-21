---
author: admin
comments: false
date: 2011-05-19 09:23:30+00:00
layout: post
link: https://witr.net/quotation/?p=514
slug: find-out-oracle-db-service-name-or-sid
title: find out oracle DB service name or SID
wordpress_id: 514
categories:
- oracle
---


If I have system access to oracle DB, and want to find out the service name


<blockquote>
> sqlplus system
password: XXXX
SQL> select sys_context('userenv','instance_name') from dual;
</blockquote>



output


<blockquote>
SYS_CONTEXT('USERENV','INSTANCE_NAME')
--------------------------------------------------
MY_INSTANCE_NAME
</blockquote>



Now, to find out SID


<blockquote>
SQL> select sys_context('userenv','sid') from dual;
</blockquote>




