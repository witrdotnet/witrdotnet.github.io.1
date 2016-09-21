---
author: admin
comments: false
date: 2012-05-02 08:03:00+00:00
layout: post
link: https://witr.net/quotation/?p=93
slug: requete-qui-cherche-dans-tous-les-composants-apex-a-ameliorer-constemment
title: requête qui cherche dans tous les composants apex (à améliorer constemment)
wordpress_id: 93
categories:
- apex
- oracle
---


  
May 2, 2012  
  
--accept search_text prompt "Enter search text: "  


<blockquote>select application_id, page_id, 'Region' objtype, region_name obj_name, region_source source  
from   apex_application_page_regions  
where lower(region_source) like lower('%&search;_text%')  
  
UNION ALL  
select application_id, page_id, 'Region (condition)' obj_type, region_name obj_name, to_clob('--EXPR1:'||CHR(13)||CHR(10)||condition_expression1||CHR(13)||CHR(10)||CHR(13)||CHR(10)||'--EXPR2:'||CHR(13)||CHR(10) || condition_expression2) source  
from   apex_application_page_regions  
where  lower(condition_expression1 || ' ' || condition_expression2) like  lower('%&search;_text%')  
  
UNION ALL  
select application_id, page_id, 'Item' obj_type, item_name obj_name, to_clob(item_source) source  
from   apex_application_page_items  
where  lower(item_source) like  lower('%&search;_text%')  
  
UNION ALL  
select application_id, page_id, 'Item (condition)' obj_type, item_name obj_name, to_clob('--EXPR1:'||CHR(13)||CHR(10)||condition_expression1||CHR(13)||CHR(10)||CHR(13)||CHR(10)||'--EXPR2:'||CHR(13)||CHR(10) || condition_expression2) source  
from   apex_application_page_items  
where  lower(condition_expression1 || ' ' || condition_expression2) like  lower('%&search;_text%')  
  
UNION ALL  
select application_id, page_id, 'Item (default value)' obj_type, item_name obj_name, to_clob(item_default) source  
from   apex_application_page_items  
where  lower(item_default) like  lower('%&search;_text%')  
  
UNION ALL  
select application_id, page_id, 'Item (lov)' obj_type, item_name obj_name, to_clob(lov_definition) source  
from   apex_application_page_items  
where  lower(lov_definition) like  lower('%&search;_text%')  
  
UNION ALL  
select application_id, page_id, 'Item (post computation)' obj_type, item_name obj_name, to_clob(source_post_computation) source  
from   apex_application_page_items  
where  lower(source_post_computation) like  lower('%&search;_text%')  
  
UNION ALL  
select application_id, page_id, 'Item (readOnly condition)' obj_type, item_name obj_name, to_clob(read_only_condition_exp1) source  
from   apex_application_page_items  
where  lower(read_only_condition_exp1) like  lower('%&search;_text%')  
  
UNION ALL  
select application_id, page_id, 'Process' obj_type, process_name obj_name, process_source source  
from   apex_application_page_proc  
where  lower(process_source) like  lower('%&search;_text%')  
  
UNION ALL  
select application_id, page_id, 'Process (condition)' obj_type, process_name obj_name, to_clob('--EXPR1:'||CHR(13)||CHR(10)||condition_expression1||CHR(13)||CHR(10)||CHR(13)||CHR(10)||'--EXPR2:'||CHR(13)||CHR(10) || condition_expression2) source  
from   apex_application_page_proc  
where  lower(condition_expression1 || ' ' || condition_expression2) like  lower('%&search;_text%')  
  
UNION ALL  
select application_id, page_id, 'Calcul' obj_type, execution_sequence||' '||item_name obj_name, to_clob(computation) source  
from   apex_application_page_comp  
where  lower(computation) like  lower('%&search;_text%')  
  
UNION ALL  
select application_id, page_id, 'Calcul (condition)' obj_type, execution_sequence||' '||item_name obj_name, to_clob('--EXPR1:'||CHR(13)||CHR(10)||condition_expression1||CHR(13)||CHR(10)||CHR(13)||CHR(10)||'--EXPR2:'||CHR(13)||CHR(10) || condition_expression2) source  
from   apex_application_page_comp  
where  lower(condition_expression1 || ' ' || condition_expression2) like  lower('%&search;_text%')  
  
UNION ALL  
select application_id, page_id, 'Branch' obj_type, TO_CHAR(process_sequence) obj_name, to_clob(branch_action) source  
from   apex_application_page_branches  
where  lower(branch_action) like  lower('%&search;_text%')  
  
UNION ALL  
select application_id, page_id, 'Branch (condition)' obj_type, to_char(process_sequence) obj_name, to_clob('--EXPR1:'||CHR(13)||CHR(10)||condition_expression1||CHR(13)||CHR(10)||CHR(13)||CHR(10)||'--EXPR2:'||CHR(13)||CHR(10) || condition_expression2) source  
from   apex_application_page_branches  
where  lower(condition_expression1 || ' ' || condition_expression2) like  lower('%&search;_text%')  
  
UNION ALL  
select application_id, page_id, 'Button (condition)' obj_type, BUTTON_SEQUENCE || ' ' || BUTTON_NAME obj_name, to_clob('--EXPR1:'||CHR(13)||CHR(10)||condition_expression1||CHR(13)||CHR(10)||CHR(13)||CHR(10)||'--EXPR2:'||CHR(13)||CHR(10) || condition_expression2) source  
from   apex_application_page_buttons  
where  lower(condition_expression1 || ' ' || condition_expression2) like  lower('%&search;_text%')  
  
UNION ALL  
select application_id, page_id, 'Validation' obj_type, VALIDATION_NAME obj_name, to_clob('--EXPR1:'||CHR(13)||CHR(10)||validation_expression1||CHR(13)||CHR(10)||CHR(13)||CHR(10)||'--EXPR2:'||CHR(13)||CHR(10) || validation_expression2) source  
from   apex_application_page_val  
where  lower(validation_expression1 || ' ' || validation_expression2) like  lower('%&search;_text%')  
  
UNION ALL  
select application_id, page_id, 'Validation (condition)' obj_type, VALIDATION_NAME obj_name, to_clob('--EXPR1:'||CHR(13)||CHR(10)||condition_expression1||CHR(13)||CHR(10)||CHR(13)||CHR(10)||'--EXPR2:'||CHR(13)||CHR(10) || condition_expression2) source  
from   apex_application_page_val  
where  lower(condition_expression1 || ' ' || condition_expression2) like  lower('%&search;_text%')  
  
UNION ALL  
select ap.application_id application_id, -1 page_id, 'application_process' obj_type, to_char(ap.PROCESS_NAME) obj_name, process source  
  from apex_application_processes ap  
where  lower(ap.process) like  lower('%&search;_text%')  
  
UNION ALL  
select aa.application_id application_id, -1 page_id, 'authorization model' obj_type, to_char(aa.authorization_scheme_name) obj_name, to_clob(aa.scheme) source  
  from apex_application_authorization aa  
where  lower(aa.scheme) like  lower('%&search;_text%')  
  
---------------------------------------------------------------------  
---------------------------------------------------------------------  
---- replace authorization model request by the following if APEX 4  
/*  
  
UNION ALL  
select aa.application_id application_id, -1 page_id, 'authorization model' obj_type, to_char(aa.authorization_scheme_name) obj_name,  
       to_clob(aa.attribute_01 || ' || ' || aa.attribute_02 || ' || ' ||aa.attribute_03 || ' || ' ||aa.attribute_04 || ' || ' ||aa.attribute_05 || ' || ' ||  
               aa.attribute_06 || ' || ' || aa.attribute_07 || ' || ' ||aa.attribute_08 || ' || ' ||aa.attribute_09 || ' || ' ||aa.attribute_10 || ' || ' ||  
               aa.attribute_11 || ' || ' || aa.attribute_12 || ' || ' ||aa.attribute_13 || ' || ' ||aa.attribute_14 || ' || ' ||aa.attribute_15  
       ) source  
  from apex_application_authorization aa  
where  lower(aa.attribute_01) like  lower('%&search;_text%') OR  
       lower(aa.attribute_02) like  lower('%&search;_text%') OR  
       lower(aa.attribute_03) like  lower('%&search;_text%') OR  
       lower(aa.attribute_04) like  lower('%&search;_text%') OR  
       lower(aa.attribute_05) like  lower('%&search;_text%') OR  
       lower(aa.attribute_06) like  lower('%&search;_text%') OR  
       lower(aa.attribute_07) like  lower('%&search;_text%') OR  
       lower(aa.attribute_08) like  lower('%&search;_text%') OR  
       lower(aa.attribute_09) like  lower('%&search;_text%') OR  
       lower(aa.attribute_10) like  lower('%&search;_text%') OR  
       lower(aa.attribute_11) like  lower('%&search;_text%') OR  
       lower(aa.attribute_12) like  lower('%&search;_text%') OR  
       lower(aa.attribute_13) like  lower('%&search;_text%') OR  
       lower(aa.attribute_14) like  lower('%&search;_text%') OR  
       lower(aa.attribute_15) like  lower('%&search;_text%')  

> 
>   

> 
> 
  
*/  
  
UNION ALL  
select alov.application_id application_id, -1 page_id, 'lov' obj_type, to_char(alov.list_of_values_name) obj_name, to_clob(alov.list_of_values_query) source  
  from apex_application_lovs alov  
where  lower(alov.list_of_values_query) like  lower('%&search;_text%')  
  
ORDER BY 1,2,3,4  
  
</blockquote>



