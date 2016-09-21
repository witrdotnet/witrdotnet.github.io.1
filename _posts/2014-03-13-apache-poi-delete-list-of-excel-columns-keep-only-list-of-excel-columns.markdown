---
author: admin
comments: false
date: 2014-03-13 09:21:36+00:00
layout: post
link: https://witr.net/quotation/?p=449
slug: apache-poi-delete-list-of-excel-columns-keep-only-list-of-excel-columns
title: 'Apache POI : delete list of excel columns / keep only list of excel columns'
wordpress_id: 449
categories:
- java
---


First you must got code from [here](http://quote.witr.net/?p=444)

Remove some columns with provided headers

    
    
        public void deleteColumnsWithHeader(String columnHeader){
            SXSSFSheet sheet = (SXSSFSheet)sh;
            Row row     = sheet.getRow( 0 );
            if ( row == null ){
                return;
            }
    
            int lastColumn = row.getLastCellNum();
    
            for ( int x=lastColumn; x >= 0; x-- ){
                Cell headerCell    = row.getCell(x);
                if ( headerCell != null && headerCell.getStringCellValue() != null && 
                     headerCell.getStringCellValue().equalsIgnoreCase(columnHeader)){
                    deleteColumn(x);
                }
            }
        }
    


Keep only columns with provided headers

    
    
        public void keepOnlyColumnsWithHeaders(List<string> columnHeaders){
            SXSSFSheet sheet = (SXSSFSheet)sh;
            Row row     = sheet.getRow( 0 );
            if ( row == null ){
                return;
            }
    
            int lastColumn = row.getLastCellNum();
    
            for ( int x=lastColumn; x >= 0; x-- ){
                Cell headerCell    = row.getCell(x);
                if ( headerCell != null && headerCell.getStringCellValue() != null && 
                     !columnHeaders.contains(headerCell.getStringCellValue())){
                    deleteColumn(x);
                }
            }
        }
    



