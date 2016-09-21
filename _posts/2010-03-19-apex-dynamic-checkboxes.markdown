---
author: admin
comments: false
date: 2010-03-19 08:31:04+00:00
layout: post
link: https://witr.net/quotation/?p=465
slug: apex-dynamic-checkboxes
title: Apex dynamic checkboxes
wordpress_id: 465
categories:
- apex
- oracle
- pl/sql
---


A way to display and handle checkboxes apex items by code

Display check boxes from select request : Create Region with PL/SQL Type and with following source

    
    
    declare 
    
        cursor chk_cur is SELECT 
            id, label
        FROM t_witr
        ORDER BY label;
    
        ind integer := 1;
        l_chk_selected_ids varchar2(3000) := null;
        l_check_state varchar2(30) := 'CHECKED';
    
    begin
    
        l_chk_selected_ids := :P1_CHK_SELECTED_IDS;
    
        htp.prn('<h2>Items selection</h2>');
        htp.prn('<table style="width:100%">');
        for col in chk_cur loop
            if ind mod 2 > 0 then 
                htp.prn('<tr><td>');
            else
                htp.prn('<td>');
            end if;
            if l_chk_selected_ids is not null and length(trim(l_chk_selected_ids)) > 0 and instr(l_chk_selected_ids,'#!' || col.id || '#!') <= 0 then
              l_check_state := 'UNCHECKED';
            else
              l_check_state := 'CHECKED';
            end if;
            htp.prn(apex_item.checkbox(1,col.id,l_check_state));
            htp.prn('<label class="chkLabel">'||col.label||'</label>');
            if ind mod 2 > 0 then 
                htp.prn('</td>');
            else
                htp.prn('</td></tr>');
            end if;
    
            ind := ind +1;
        end loop;
        htp.prn('</table>');
    
    end;
    



Create button submit, and then create process executed after submit to save items selection state like following

    
    
    declare
      l_chk_selected_ids varchar2(3000);
    
    begin
      FOR i in 1..APEX_APPLICATION.G_F01.count
      LOOP
        l_chk_selected_ids := l_chk_selected_ids || '#!' || APEX_APPLICATION.G_F01(i) || '#!';
      END LOOP;
     :P1_CHK_SELECTED_IDS := l_chk_selected_ids;
    end;
    



