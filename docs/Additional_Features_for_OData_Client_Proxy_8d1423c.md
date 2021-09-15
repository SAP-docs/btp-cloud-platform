<!-- loio8d1423cd45134e8ba9738d94cefc7264 -->

# Additional Features for OData Client Proxy

OData Client Proxy provides the following additional features:

<a name="loio8d1423cd45134e8ba9738d94cefc7264__table_n4t_n43_vnb"/>


<table>
<tr>
<th>

Feature



</th>
<th>

Description



</th>
<th>

Available as of Release



</th>
</tr>
<tr>
<td>

Delete delta links In case of a new initial load



</td>
<td>

If you want to delete delta links in case of new initial load, you can use method `DELETE_DELTA_LINK()` of class `CL_CP_DELTA_REQU_CONFIG`.



</td>
<td>

 SAP BTP, ABAP environment 2105



</td>
</tr>
<tr>
<td>

Update Collections



</td>
<td>

You can update collections on client side to support Master Data Integration \(MDI\).



</td>
<td>

 SAP BTP, ABAP environment 2105



</td>
</tr>
<tr>
<td>

Add custom query options



</td>
<td>

You can add custom query options using the following interface and class:

-   /IWBEP/IF\_CP\_REQUEST\_READ\_LIST

    Added method implementation: set\_custom\_query\_options

-   /IWBEP/CL\_CP\_REQUEST

    Added implementation: set\_custom\_query\_options

    Expanded to\_uri\_representation to handle custom\_query\_options




</td>
<td>

 SAP BTP, ABAP environment 2105



</td>
</tr>
<tr>
<td>

Create a new version of a stored delta link



</td>
<td>

You can create a new version of a stored delta link to be used by a newly created request using the USE\_DELTA\_LINK\(\) method.



</td>
<td>

 SAP BTP, ABAP environment 2105



</td>
</tr>
<tr>
<td>

Invoking V2 Functions via *Local Client Proxy*.



</td>
<td>

You can use the *Local Client Proxy* to invoke V2 Functions.



</td>
<td>

 SAP BTP, ABAP environment 2102



</td>
</tr>
<tr>
<td>

Range conversion exit of a property with $filter.



</td>
<td>

You can use the USE\_RANGES\_4\_FILTER\_CONVERSION model feature to change the filter expression determination logic.

This applies, when a model feature is set in MPC\_EXT, when the range conversion exit for a property in an OData service exists, and when this property is used with a filter condition

Supported request formation example: /sap/opu/odata/sap/Northwind/Customers$filter=startswith\(Name,’Alfr’\)

Not supported request formation example: /sap/opu/odata/sap/Northwind/Customers$filter=startswith\(Name,’Alfr’\) eq true



</td>
<td>

 SAP BTP, ABAP environment 2102



</td>
</tr>
<tr>
<td>

Writing statistics for tests running with the *Local Client Proxy* to enable coverage reporting.



</td>
<td>

For the *Local Client Proxy* V2 and V4, the `iv_do_write_traces` method in class `/IWBEP/CL_CP_CLIENT_PROXY_FACT` parameter controls writing statistics.

The constructor of `/IWBEP/CL_CP_CLIENT_PROXY` contains this parameter.

The existing method `/IWBEP/CL_CP_LOGGER~LOG_REQUEST_HTTP` for writing the payload trace allowss writing statistics.

When an operation is executed and `iv_do_write_traces` is set to true, the gateway specific statistic will be filled.



</td>
<td>

SAP BTP, ABAP environment

2102



</td>
</tr>
<tr>
<td>

Filtering by conversion exits.



</td>
<td>

For OData V4, filtering by correctly applying conversion exits \(e.g. CUNIT\), is supported.



</td>
<td>

 SAP BTP, ABAP environment 2102



</td>
</tr>
<tr>
<td>

V4 local consumption in *Local Client Proxy*.



</td>
<td>

Example for the use of method `CREATE_V4_LOCAL_PROXY` in class `CL_WEB_ODATA_CLIENT_FACTORY`:

> ### Sample Code:  
> ```
> TRY.
>     lo_client_proxy = cl_web_odata_client_factory=>create_v4_local_proxy( ls_v4_service_key ).
>  
>   CATCH /iwbep/cx_gateway INTO lx_gateway.
>     out->write( lx_gateway->get_text( ) ).
>     EXIT.
> ENDTRY.
>  
>  
> out->write( '****** GET Teams ******' ).
>  
> TRY.
>     lo_list_resource = lo_client_proxy->create_resource_for_entity_set( 'TEAMS' ).
>     lo_list_request  = lo_list_resource->create_request_for_read( ).
>     lo_list_response = lo_list_request->execute( ).
>     lo_list_response->get_business_data( IMPORTING et_business_data = lt_team ).
>  
>   CATCH /iwbep/cx_gateway INTO lx_gateway.
>     out->write( lx_gateway->get_text( ) ).
> ENDTRY.
> ```



</td>
<td>

 SAP BTP, ABAP environment 2102



</td>
</tr>
<tr>
<td>

 *Deep Create* for V4 local consumption.



</td>
<td>

 *Deep Create* for V4 local consumption is combined with partial business data/provided properties. For more information, see classes `/IWBEP/CL_CP_DATA_DESC_NODE` and`/IWBEP/CL_V4_EXPAND_NODE` 



</td>
<td>

SAP BTP, ABAP environment 2102



</td>
</tr>
<tr>
<td>

 *Local Client Proxy* consumption supports $batch.



</td>
<td>

The *OData Client Proxy* supports $batch changesets for the local consumption of a V2 service.

> ### Sample Code:  
> Example for a unit test:
> 
> ```
> lo_request_batch       = mo_client_proxy->create_request_for_batch( ).
> lo_request_changeset   = lo_request_batch->create_request_for_changeset( ).
> lo_request_batch->add_request( lo_request_changeset ). 
> lo_request_update      = mo_resource_team->create_request_for_update( /iwbep/if_cp_request_update=>gcs_update_semantic-patch
>                                         )->set_business_data( is_business_data     = ls_team
>                                                               it_provided_property = VALUE #( ( `NAME` ) ) ).
> lo_request_changeset->add_request( lo_request_update ).
>   
> lo_request_batch->execute( ).
>   
> lo_request_update->check_execution( )->get_response( )->get_business_data( IMPORTING es_business_data = ls_team_act ).
> ```

There are two options available in the V2 runtime how a changeset is processed:

-   Normal processing: The DPC is called per modifying operation and the V2 runtime handles the LUW \(logical unit of work\) defined by the changeset.

-   Deferred processing: The DPC receives all changeset operations in the single method call`/IWBEP/IF_MGW_APPL_SRV_RUNTIME~CHANGESET_PROCESS`.



</td>
<td>

 SAP BTP, ABAP environment 2102



</td>
</tr>
<tr>
<td>

Catalog service supports recommended services.



</td>
<td>

The `RecommendedServices` entity set returns all V4 services registered in the backend or only subset of recommended ones:

GET /sap/opu/odata4/iwfnd/config/default/iwfnd/catalog/0002/ServiceGroups?$expand=DefaultSystem\($expand=RecommendedServices\)



</td>
<td>

 SAP BTP, ABAP environment 2102



</td>
</tr>
</table>

