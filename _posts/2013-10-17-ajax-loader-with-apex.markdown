---
author: admin
comments: false
date: 2013-10-17 11:18:00+00:00
layout: post
link: https://witr.net/quotation/?p=16
slug: ajax-loader-with-apex
title: ajax loader with APEX
wordpress_id: 16
categories:
- ajax
- apex
- oracle
---




### 1. Prerequisites in plsql oracle packages




#### 1.1. Stored procedure GENERATE_REPORT



    
    
    procedure GENERATE_REPORT(p_report_id in number) is
    begin
    	--------------
    	-- long time process to generate report
    	-- blabla
    	-- babla
    	----------------
    	
    	update REPORT
    		set STATUS = 'FINISH'
    	where REPORT_ID = p_report_id;
    	
    	exception when others then
    		update REPORT
    			set STATUS = 'ERROR'
    		where REPORT_ID = p_report_id;	
    end;
    




#### 1.2. Stored function START_GENERATE_REPORT



    
    
    function START_GENERATE_REPORT() return number is
    	l_report_id number;
    	l_dummy     number;
    begin
    	l_report_id := SEQ_REPORT.nextval;
    	insert into 
    	REPORT(REPORT_ID,STATUS)
    	VALUES(l_report_id,'GENRATING');
    	
    	DBMS_JOB.SUBMIT(l_dummy,'begin GENERATE_REPORT('||l_report_id||'); end;');
    	
    	return l_report_id;
    end;
    




#### 1.3. Stored function GET_REPORT_STATUS



    
    
    function GET_REPORT_STATUS(p_report_id in number) return varchar2 is
     l_status varchar2(100);
    begin
    	select STATUS into l_status
    		from REPORT
    	where REPORT_ID = p_report_id;
    	
    	return l_status;
    	
    	exception when others then
    		return 'ERROR';
    end;
    




### 2. APEX application

  

HIDDEN TEXT ELEMENT 'PAGE_REPORT_ID'  

BUTTON ELEMENT 'generate': button click submits page  

PAGE PROCESS ELEMENT 'processGenerate': activated on 'generate' button click  


    
    
    declare
      l_report_id number;
    begin
      l_report_d := START_GENERATE_REPORT();
      :PAGE_REPORT_ID := l_report_d;
    end;
    


HTML FORM ELEMENT 'loader'  
- condition : PAGE_REPORT_ID content is not null  
- content :  


    
    
    <div id="divLoader"></div>
    <script language="javascript">
      refreshReportLoader();
    </script>
    


APPLICATION PROCESS ELEMENT : PROCESS_REPORT_STATUS  
In apex go to application process and create new process. be sure you select "On Demand" as Point property of your process. 

    
    
    declare
    	l_param_report_id varchar2(100);
    	l_result_status   varchar2(100);
    begin
    	owa_util.mime_header('text', FALSE );
    	htp.p('Cache-Control: no-cache');
    	htp.p('Pragma: no-cache');
    	owa_util.http_header_close;	
    	
    	l_param_report_id := wwv_flow.g_x01;
    	l_result_status := GET_REPORT_STATUS(to_number(l_param_report_id));
    	htp.prn(l_result_status);
    end;
    


IN PAGE HEADER  
put javascript following javascript function :  


    
    
    function refreshReportLoader(){
    	var get = new htmldb_Get(null, $v('pFlowId'), 'APPLICATION_PROCESS=PROCESS_REPORT_STATUS',0);	
    	get.addParam('x01',$v('P_REPORT_ID'));
    	gStatus = get.get('TEXT');
    
    	var loader = document.getElementById("divLoader");
    	loader.innerHTML= gStatus ;
    	
    	if(!gStatus == 'FINISH' && !gStatus == 'ERROR'){
    		 setTimeout(function(){refreshReportLoader()},3000);
    	}
    }
    




### 3. how to use


click on button 'generate' and see the loader div which must change content according to REPORT.STATUS  


  




