---
author: admin
comments: false
date: 2011-06-08 09:18:54+00:00
layout: post
link: https://witr.net/quotation/?p=682
slug: onetomany-association-that-dont-query-any-element
title: 'OneToMany association : hql query returns no results'
wordpress_id: 682
categories:
- hibernate
- java
---


Problem: hql query retruns null or empty result while sql corresponding query returns some resultsets.
If the target hibernate Java Bean have an EmbeddedId be sure that the AttributeOverrides didn't include a nullable column attribute.
If so remove these nullable columns attributes from embedded id and put them directly in the bean as Bean variable properties. And this will fix problem


### Wrong Id definition



    
    
    @Entity
    @Table(name="WITR_MARIAGE", uniqueConstraints = @UniqueConstraint(columnNames={"CUSTOMER_ID", "WITR_HUSBAND_ID", "WITR_WIFE_ID"}) )
    public class WitrMariage  implements java.io.Serializable {
    
        private WitrMariageId id;
        private WitrHusband witrHusband;
        private WitrWife witrWife;
    
        @EmbeddedId
        @AttributeOverrides( {
                @AttributeOverride(name="customerId", column=@Column(name="CUSTOMER_ID", nullable=false, precision=22, scale=0) ),
                @AttributeOverride(name="witrHusbandId", column=@Column(name="WITR_HUSBAND_ID", nullable=false, precision=22, scale=0) ),
                @AttributeOverride(name="witrWifeId", column=@Column(name="WITR_WIFE_ID", nullable=false, precision=22, scale=0) ),
                @AttributeOverride(name="sort", column=@Column(name="SORT", precision=22, scale=0) ) } )
        public WitrMariageId getId() {
            return this.id;
        }
    
        public void setId(WitrMariageId id) {
            this.id = id;
        }
    
        /*
         *   WitrHusband getter & setter
         *   WitrWife getter & setter
         */
    
    }
    




### Right Id definition



    
    
    @Entity
    @Table(name="WITR_MARIAGE", uniqueConstraints = @UniqueConstraint(columnNames={"CUSTOMER_ID", "WITR_HUSBAND_ID", "WITR_WIFE_ID"}) )
    public class WitrMariage  implements java.io.Serializable {
    
        private WitrMariageId id;
        private WitrHusband witrHusband;
        private WitrWife witrWife;
        private long sort;
    
        @EmbeddedId
        @AttributeOverrides( {
                @AttributeOverride(name="customerId", column=@Column(name="CUSTOMER_ID", nullable=false, precision=22, scale=0) ),
                @AttributeOverride(name="witrHusbandId", column=@Column(name="WITR_HUSBAND_ID", nullable=false, precision=22, scale=0) ),
                @AttributeOverride(name="witrWifeId", column=@Column(name="WITR_WIFE_ID", nullable=false, precision=22, scale=0) ) } )
        public WitrMariageId getId() {
            return this.id;
        }
    
        public void setId(WitrMariageId id) {
            this.id = id;
        }
    
        /*
         *   WitrHusband getter & setter
         *   WitrWife getter & setter
         *   sort getter & setter
         */
    
    }
    



