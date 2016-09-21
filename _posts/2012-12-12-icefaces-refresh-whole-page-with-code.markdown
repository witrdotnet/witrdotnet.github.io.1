---
author: admin
comments: false
date: 2012-12-12 16:27:51+00:00
layout: post
link: https://witr.net/quotation/?p=415
slug: icefaces-refresh-whole-page-with-code
title: 'icefaces : refresh whole page with code'
wordpress_id: 415
categories:
- icefaces
- jsf
---



    
    
         public void refreshPage() {
            FacesContext context = FacesContext.getCurrentInstance();
            Application application = context.getApplication();
            ViewHandler viewHandler = application.getViewHandler();
            UIViewRoot viewRoot = viewHandler.createView(context, context.getViewRoot().getViewId());
            context.setViewRoot(viewRoot);
        }
    



