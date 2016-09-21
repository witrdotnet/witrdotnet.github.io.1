---
author: admin
comments: false
date: 2014-03-04 11:18:58+00:00
layout: post
link: https://witr.net/quotation/?p=428
slug: oracle-db-be-ware-when-specifying-clumn-max-length
title: 'Oracle DB : Beware when specifying column max length'
wordpress_id: 428
categories:
- oracle
---


To create table STUDENT with single column NAME which must not excceed 6 characters, you may type the following

    
    
    CREATE TABLE STUDENT
      (
        NAME VARCHAR2 (6)
      );
    


But this is wrong if NLS_LENGTH_SEMANTICS=BYTE (default value) : Typing VARCHAR2(6) means 6 bytes and not 6 characters.
In this case "Claude" will be accepted but not "Noémie", because 'é' is encoded with 2 bytes and the sum will exceed 6 bytes.

The right way to specify column max length is as follow 

    
    
    CREATE TABLE STUDENT
      (
        NAME VARCHAR2 (6 CHAR)
      );
    



NLS_LENGTH_SEMANTICS enables you to create CHAR and VARCHAR2 columns using either byte or character length semantics. Existing columns are not affected.

NCHAR, NVARCHAR2, CLOB, and NCLOB columns are always character-based. You may be required to use byte semantics in order to maintain compatibility with existing applications.

NLS_LENGTH_SEMANTICS does not apply to tables in SYS and SYSTEM. The data dictionary always uses byte semantics.

Get and/or set NLS_LENGTH_SEMANTICS value

    
    
    -- get NLS_LENGTH_SEMANTICS value
    SELECT * FROM NLS_database_PARAMETERS WHERE PARAMETER = 'NLS_LENGTH_SEMANTICS';
    -- set NLS_LENGTH_SEMANTICS to CHAR
    ALTER system SET NLS_LENGTH_SEMANTICS=CHAR; -- restart to take effect
    



