---
author: admin
comments: false
date: 2012-11-12 16:30:41+00:00
layout: post
link: https://witr.net/quotation/?p=417
slug: icefaces-force-refresh-a-portion-of-page
title: 'icefaces : force refresh a portion of page'
wordpress_id: 417
categories:
- icefaces
- jsf
---



    
    
        public void refreshUI(String componentId) {
            UIComponent uiComp = BaseBean.findComponentInRoot(componentId);
            if (uiComp != null) {
                uiComp.getChildren().clear();
            }
        }
    
        public static UIComponent findComponentInRoot(String id) {
            UIComponent component = null;
    
            FacesContext facesContext = FacesContext.getCurrentInstance();
            if (facesContext != null) {
                UIComponent root = facesContext.getViewRoot();
                component = findComponent(root, id);
            }
    
            return component;
        }
    
        public static UIComponent findComponent(UIComponent base, String id) {
            if (id.equals(base.getId())) {
                return base;
            }
    
            UIComponent kid = null;
            UIComponent result = null;
            Iterator<uicomponent> kids = base.getFacetsAndChildren();
            while (kids.hasNext() && (result == null)) {
                kid = kids.next();
                if (id.equals(kid.getId())) {
                    result = kid;
                    break;
                }
                result = findComponent(kid, id);
                if (result != null) {
                    break;
                }
            }
            return result;
        }
    



