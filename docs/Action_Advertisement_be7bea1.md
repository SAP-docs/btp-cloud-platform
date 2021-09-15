<!-- loiobe7bea10609a40d8a4cc57cedd509cd2 -->

# Action Advertisement

In the course of data provider class \(DPC\) development you can control if an action is available or not for an entity instance in order to prevent calling the action. Thus you can specify instance-specific operations. A property of an entity type points to a bound action, and you can make bound actions available. There could be actions which are present during runtime but which you might not want to advertise. Typical examples are the approval or rejection actions for workflow items or editing for draft actions.

For this method `USE_FOR_OPERATION_ADVERTISING` of interface `/IWBEP/IF_V4_MED_PRIM_PROP` is available: With this method you can determine the visibility of the action which can have the following status:

-   Constant `/IWBEP/IF_V4_RUNTIME_TYPES=>GCS_ADVERTISE_INDICATOR-ADVERTISE_OMIT` 

    Omit action for entity instance, not visible.

-   Constant `/IWBEP/IF_V4_RUNTIME_TYPES=>GCS_ADVERTISE_INDICATOR-ADVERTISE_AVAILABLE` 

-   No constant value.

    Initial property value.


Action advertisement always works in the same namespace and for the same entity type.

> ### Sample Code:  
> Operation advertising for SetAvailable and SetOccupied
> 
> ```
>  . .
> 
> * Operation advertising for SetAvailable and SetOccupied   
> 
> lo_property = lo_entity_type->create_prim_property( 'OA_SET_IS_AVAILABLE' ) ##no_text.
> 
> lo_property->use_for_operation_advertising( 'SET_IS_AVAILABLE' ). 
> 
> lo_property->set_edm_type( /iwbep/if_v4_med_element=>gcs_edm_data_types-string ). 
> 
> lo_property->set_is_technical( ). 
> 
>  
> 
> lo_property = lo_entity_type->create_prim_property( 'OA_SET_IS_OCCUPIED' ) ##no_text.
> 
> lo_property->use_for_operation_advertising( 'SET_IS_OCCUPIED' ).
> 
> lo_property->set_edm_type( /iwbep/if_v4_med_element=>gcs_edm_data_types-string ).
> 
> lo_property->set_is_technical( ).
> 
>  . . .
> ```

> ### Sample Code:  
> Payload of operation advertisment
> 
> ```
> 
> Request
> 
> GET EMPLOYEES('1') HTTP/1.1
> 
> 
> 
> Response
> 
> HTTP/1.1 200 OK
> 
>  
> 
> {
> 
>     "@odata.context" : "$metadata#EMPLOYEES/$entity",
> 
>     "@odata.etag" : "W/\"19770724000000.0000000\"",
> 
>     "#com.sap.gateway.default.iwbep.tea_busi.v0001.AcSetIsOccupied" : {},
> 
>     "ID" : "1",
> 
>     . . . ,
> 
>     "STATUS" : "Available"
> 
> }
> 
> ```

Actions can also be specified for the payload in order to control which actions should be advertised.

When selecting properties you can also select actions via IDs.



<a name="loiobe7bea10609a40d8a4cc57cedd509cd2__section_ttm_3kf_v1b"/>

## Selecting Advertised Actions Using $select

You can select individual advertised actions \(like properties\) using system query option `$select` with the qualified action name. For example, `$select=com.sap.gateway.default.iwbep.tea_busi.v0001.AcSetIsAvailable`.

For each selected action its advertising property is added to the list of selected properties in the corresponding select node.

Selecting all operations in a specified namespace is not supported and results in a 501 Not Implemented response.

Note that selecting all properties \(using `$select=*`\) does not automatically select advertised actions.

