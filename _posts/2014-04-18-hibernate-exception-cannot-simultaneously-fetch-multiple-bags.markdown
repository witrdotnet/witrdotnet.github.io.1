---
author: admin
comments: false
date: 2014-04-18 13:44:10+00:00
layout: post
link: https://witr.net/quotation/?p=486
slug: hibernate-exception-cannot-simultaneously-fetch-multiple-bags
title: 'Hibernate exception : cannot simultaneously fetch multiple bags'
wordpress_id: 486
categories:
- exception
- hibernate
- java
---




## Problem


Exception class : org.hibernate.loader.MultipleBagFetchException
Exception : cannot simultaneously fetch multiple bags


## Solution


Use @LazyCollection(LazyCollectionOption.FALSE) rather than fetch=FetchType.EAGER
Annotation @LazyCollection(LazyCollectionOption.FALSE) makes that collecion is loaded like with FetchType.EAGER and you can use it on two and more collections.


## Example


**Initial Code : Works with lazy fetch type**

    
    
    public class WitrEntity{
    
        private Set<witrentitylabel> witrEntityLabels = new HashSet(0);
    
        [...]
    
        @OneToMany(fetch=FetchType.LAZY, mappedBy="witrEntity")
        public Set<witrentitylabel> getWitrEntityLabels() {
            return this.witrEntityLabels;
        }
    
    }
    
    public class WitrEntityLabel{
    
        private WitrEntity witrEntity;
    
        [...]
    
        @ManyToOne(fetch=FetchType.LAZY)
        @JoinColumn(name="WITR_ENTITY_ID", nullable=false, insertable=false, updatable=false)
        public WitrEntity getWitrEntity() {
            return this.witrEntity;
        }
    
    }
    



**Wrong manipulation : wanna set fetch type to eager**

    
    
    public class WitrEntity{
    
        private Set<witrentitylabel> witrEntityLabels = new HashSet(0);
    
        [...]
    
        @OneToMany(fetch=FetchType.EAGER, mappedBy="witrEntity") // THIS IS THE CAUSE OF EXCEPTION
        public Set<witrentitylabel> getWitrEntityLabels() {
            return this.witrEntityLabels;
        }
    
    }
    
    public class WitrEntityLabel{
    
        private WitrEntity witrEntity;
    
        [...]
    
        @ManyToOne(fetch=FetchType.LAZY)
        @JoinColumn(name="WITR_ENTITY_ID", nullable=false, insertable=false, updatable=false)
        public WitrEntity getWitrEntity() {
            return this.witrEntity;
        }
    
    }
    



**Solution : if you want to force loading collection**

    
    
    public class WitrEntity{
    
        private Set<witrentitylabel> witrEntityLabels = new HashSet(0);
    
        [...]
    
        @OneToMany(mappedBy="witrEntity") // delete fetch=FetchType.LAZY
        @LazyCollection(LazyCollectionOption.FALSE) // add use @LazyCollection false
        public Set<witrentitylabel> getWitrEntityLabels() {
            return this.witrEntityLabels;
        }
    }
    



