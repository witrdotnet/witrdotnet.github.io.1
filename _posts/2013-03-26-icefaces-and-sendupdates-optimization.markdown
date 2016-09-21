---
author: admin
comments: false
date: 2013-03-26 08:29:00+00:00
layout: post
link: https://witr.net/quotation/?p=79
slug: icefaces-and-sendupdates-optimization
title: icefaces and SendUpdates optimization
wordpress_id: 79
categories:
- icefaces
---


if you encounter slow rendering (on icefaces tree for example) and generally when you code using icefaces framework, be sure that any html component you write has an id or has an icefaces component as parent.  
In fact, icefaces client module send ajax request to the icefaces server module in aim to retrieve DOM changes. icefaces server module try to look for dom changes, and when each element has changed but have no id, it looks for its parent in the dom and insert all children of this parent as changed.  
  
In my case i have a page with two elements: a <div>...</div> and just after an <ice:tree>...</ice:tree>  
Unfortenatly, i don't put an id to my <div>. So when i expand one node in the <ice:tree> i got all tree nodes sent as updates elements in the icefaces ajax response.  
setting an id or converting your <div> to <ice:panelGroup> fix problem.  
  
@see  
- method computing and sending updates: com.icesoft.faces.context.PushModeSerializer -> serialize(final Document document)  
- to debug dom updates, add following in your web.xml:

    
    
        <context-param>
            <param-name>com.icesoft.faces.debugDOMUpdate</param-name>
            <param-value>true</param-value>
        </context-param>
    



