---
author: admin
comments: false
date: 2011-05-19 09:34:59+00:00
layout: post
link: https://witr.net/quotation/?p=516
slug: start-and-stop-oracle-db-sql-traces-with-shell-scripts
title: start and stop oracle DB sql traces with shell scripts
wordpress_id: 516
categories:
- oracle
---


**startSqlTrace.sh** : start sql traces

    
    
    #!/bin/bash
    echo password:
    read SYSPASS
    sqlplus system/$SYSPASS@WITRDB << FIN
    alter system set sql_trace=true;
    exit
    FIN
    



**stopSqlTrace.sh** : stop sql traces

    
    
    #!/bin/bash
    echo password:
    read SYSPASS
    sqlplus system/$SYSPASS@WITRDB << FIN
    alter system set sql_trace=false;
    exit
    FIN
    




