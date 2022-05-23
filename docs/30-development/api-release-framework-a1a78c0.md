<!-- loioa1a78c0db346406a97ce9e4d6fd61d7e -->

# API Release Framework

Find out how to set the API state.

Setting and getting API states programmatically is supported for the following objects:

-   Classes \(IF\_XCO\_AO\_CLASS\)

-   Entities of data definitions \(IF\_XCO\_CDS\_ENTITY\)

-   Domains \(IF\_XCO\_DOMAIN\)

-   Data elements \(IF\_XCO\_AD\_DATA\_ELEMENT\)

-   Function modules of function groups \(IF\_XCO\_FUNCTION\_MODULE\)

-   Interfaces \(IF\_XCO\_AO\_INTERFACE\)

-   Structures \(IF\_XCO\_AD\_STRUCTURE\)

-   Database tables \(IF\_XCO\_DATABASE\_TABLE\)

-   Table types \(IF\_XCO\_AD\_TABLE\_TYPE\)

-   Transformations \(IF\_XCO\_TRANSFORMATION\)


Each of the above interfaces defines the two methods SET\_API\_STATE and GET\_API\_STATE to programmatically set or get the API state of the represented object. For data elements, for example, this looks like:

> ### Sample Code:  
> ```abap
> 
> DATA(lo_transport) = xco_cp_cts=>transport->for( '...' ).
> DATA(lo_api_state) = xco_cp_ars=>api_state->released( VALUE #( ( xco_cp_ars=>visibility->sap_cloud_platform ) ) ).
>  
> DATA(lo_data_element) = xco_cp_abap_repository=>object->dtel->for( 'ZMY_DATA_ELEMENT' ).
> lo_data_element->set_api_state(
>   io_change_scenario = lo_transport
>   io_api_state       = lo_api_state
> ).
> ```

