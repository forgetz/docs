# request
`select * 
from sys.parameters 
inner join sys.procedures 
 on parameters.object_id = procedures.object_id
inner join sys.types 
 on parameters.system_type_id = types.system_type_id 
 AND parameters.user_type_id = types.user_type_id
where procedures.name = 'SP_SummaryForPopUpPayment'`


# response
`EXEC sp_describe_first_result_set N'SP_SummaryForPopUpPayment'`
