<!-- loioa15e1c25c393407cad5ef2ab2333672f -->

# Using a Schema Name to Refer to the Service Binding Name



In SQL statements of the SQL dialect of the ABAP SQL service, all accessed objects must be fully qualified using a schema name and an object name. As a schema name, you use the SQL service binding name. The object names are the external names of the exposed CDS objects listed in the corresponding service definition. A simple example is the following SQL statement:

> ### Sample Code:  
> ```sql
> Select * from "ZData"."OrderItems"
> where "ZData"."OrderItems"."OrderId" = 42
> 
> ```

