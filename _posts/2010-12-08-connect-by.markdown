---
author: admin
comments: false
date: 2010-12-08 17:28:00+00:00
layout: post
link: https://witr.net/quotation/?p=102
slug: connect-by
title: connect by
wordpress_id: 102
categories:
- oracle
- sql
---

We have following data table category:  
<table cellpadding="2px" border="1px" ><tbody >
<tr >
category_id
parent_id
name
sort
</tr>
<tr >

<td >10
</td>

<td >null
</td>

<td >véhicule motorisé
</td>

<td >
</td>
</tr>
<tr >

<td >11
</td>

<td >10
</td>

<td >quatre roues
</td>

<td >3
</td>
</tr>
<tr >

<td >12
</td>

<td >10
</td>

<td >sans roues
</td>

<td >1
</td>
</tr>
<tr >

<td >13
</td>

<td >10
</td>

<td >deux roues
</td>

<td >2
</td>
</tr>
</tbody></table>
  
The recursive way to query childhood relation ship data :  


<blockquote>select level, lpad(' ',level*5,' ') || t.name  
from categry t  
start with t.parent_id is null  
connect by t.parent_id = prior t.category_id  
</blockquote>

Result of query: <table ><tbody >
<tr >

<td >1
</td>

<td >véhicule motorisé
</td>
</tr>
<tr >

<td >2
</td>

<td >     quatre roues
</td>
</tr>
<tr >

<td >2
</td>

<td >     sans roues
</td>
</tr>
<tr >

<td >2
</td>

<td >     deux roues
</td>
</tr>
</tbody></table>
  
Now we have to sort children with value of column sort   


<blockquote>select level, lpad(' ',level*5,' ') || t.name  
from categry t  
start with t.parent_id is null  
connect by t.parent_id = prior t.category_id  
order siblings by t.sort </blockquote>

Result of query: <table ><tbody >
<tr >

<td >1
</td>

<td >véhicule motorisé
</td>
</tr>
<tr >

<td >2
</td>

<td >     sans roues
</td>
</tr>
<tr >

<td >2
</td>

<td >     deux roues
</td>
</tr>
<tr >

<td >2
</td>

<td >     quatre roues
</td>
</tr>
</tbody></table>

