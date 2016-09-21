---
author: admin
comments: false
date: 2014-09-19 13:58:29+00:00
layout: post
link: https://witr.net/quotation/?p=597
slug: remove-all-references-to-the-key-before-the-key-is-to-be-dropped
title: Remove all references to the key before the key is to be dropped
wordpress_id: 597
categories:
- oracle
---


if oracle db refuse to drop a constraint with message "Remove all references to the key before the key is to be dropped". It's clear that we must drop references before. But how to list these references.

Sql command bellow help to list all constraints which uses the constraint to be dropped "CONSTRAINT_TO_BE_DROPPED_NAME"


    
    
    select * from all_constraints
    where constraint_type='R' and 
    r_constraint_name='CONSTRAINT_TO_BE_DROPPED_NAME';
    



