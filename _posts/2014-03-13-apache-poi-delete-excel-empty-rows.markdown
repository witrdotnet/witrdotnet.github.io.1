---
author: admin
comments: false
date: 2014-03-13 09:32:18+00:00
layout: post
link: https://witr.net/quotation/?p=453
slug: apache-poi-delete-excel-empty-rows
title: 'Apache POI : delete excel empty rows'
wordpress_id: 453
categories:
- java
---


POI method  sheet.removeRow(), removes row cells but doesn't clear them from excel output. 
Means if you have three rows and you apply sheet.removeRow(1), you will have:
- not changed first row
- empty second row
- not changed third row

So to remove row completly you must then shift rows following.
But for some reason sheet.shiftRows() poi api method doesn't work for me.
Code bellow do it

    
    
        public void deleteEmptyRows(){
            SXSSFSheet sheet = (SXSSFSheet)sh;
            for ( int r=sheet.getLastRowNum(); r >= 0; r-- ){
                Row row     = sheet.getRow( r );
    
                // if no row exists here; then nothing to do; next!
                if ( row == null )
                    continue;
    
                int lastColumn = row.getLastCellNum();
                boolean rowToDelete = true;
                if(lastColumn > -1){
                    for ( int x=0; x < lastColumn + 1; x++ ){
                        Cell cell    = row.getCell(x);
                        if ( cell != null && cell.getStringCellValue() != null){
                            String cellTrimValue = cell.getStringCellValue().trim();
                            if(!cellTrimValue.isEmpty()){
                                rowToDelete = false;
                                break;
                            }
                        }
                    }
                }
    
                if(rowToDelete){
                    if(r == sheet.getLastRowNum()){
                        sheet.removeRow(row);
                    }else{
                        sheet.removeRow(row);
                        for(int j= r+1; j <= sheet.getLastRowNum(); j++){
                            Row rowToShift = sheet.getRow(j);
                            rowToShift.setRowNum(j-1);
                        }
                    }
                }
            }
        }
    



