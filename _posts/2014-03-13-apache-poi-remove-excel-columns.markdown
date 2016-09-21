---
author: admin
comments: false
date: 2014-03-13 09:14:12+00:00
layout: post
link: https://witr.net/quotation/?p=444
slug: apache-poi-remove-excel-columns
title: 'Apache POI : remove excel columns'
wordpress_id: 444
categories:
- java
---


Unfortunatly there was no method to remove excel columns in poi api.
Code bellow (found [here](http://pastebin.com/ff806298)) can help

    
    
        public void deleteColumn(SXSSFSheet sheet, int columnToDelete){        
            int maxColumn = 0;
            for ( int r=0; r < sheet.getLastRowNum()+1; r++ ){
                Row row     = sheet.getRow(r);
    
                // if no row exists here; then nothing to do; next!
                if ( row == null )
                    continue;
    
                // if the row doesn't have this many columns then we are good; next!
                int lastColumn = row.getLastCellNum();
                if ( lastColumn > maxColumn )
                    maxColumn = lastColumn;
    
                if ( lastColumn < columnToDelete )
                    continue;
    
                for ( int x=columnToDelete+1; x < lastColumn + 1; x++ ){
                    Cell oldCell    = row.getCell(x-1);
                    if ( oldCell != null )
                        row.removeCell( oldCell );
    
                    Cell nextCell   = row.getCell( x );
                    if ( nextCell != null ){
                        Cell newCell    = row.createCell( x-1, nextCell.getCellType() );
                        cloneCell(newCell, nextCell);
                    }
                }
            }
        }
    
        private void cloneCell( Cell cNew, Cell cOld ){
            cNew.setCellComment( cOld.getCellComment() );
            cNew.setCellStyle( cOld.getCellStyle() );
    
            switch ( cNew.getCellType() ){
                case Cell.CELL_TYPE_BOOLEAN:{
                    cNew.setCellValue( cOld.getBooleanCellValue() );
                    break;
                }
                case Cell.CELL_TYPE_NUMERIC:{
                    cNew.setCellValue( cOld.getNumericCellValue() );
                    break;
                }
                case Cell.CELL_TYPE_STRING:{
                    cNew.setCellValue( cOld.getStringCellValue() );
                    break;
                }
                case Cell.CELL_TYPE_ERROR:{
                    cNew.setCellValue( cOld.getErrorCellValue() );
                    break;
                }
                case Cell.CELL_TYPE_FORMULA:{
                    cNew.setCellFormula( cOld.getCellFormula() );
                    break;
                }
            }
    
        }
    



