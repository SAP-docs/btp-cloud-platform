<!-- loiobbb4dc2e1ed240e98a20fc73705fc46f -->

# Tenant

The XCO tenant module provides standard abstractions for querying information about tenants, in particular the tenant associated with the current ABAP session.

The central abstraction `IF_XCO_CP_TENANT` represents a tenant and is used to retrieve its public information. As of now, the following information can be retrieved:

-   ID: The ID for the tenant

-   GUID: The GUID for the tenant \(represented as an IF\_XCO\_UUID\)

-   URL: The URL of the tenant for the given URL type \(URL types are available via XCO\_CP\_TENANT=\>URL\_TYPE\)

-   Global Account ID: The ID of the global account associated with the tenant

-   Subaccount ID: The ID of the subaccount associated with the tenant


The currently active tenant can be obtained via:

```abap
DATA(lo_current_tenant) = xco_cp=>current->tenant( ).
```

Note that depending on the overall system infrastructure and setup a current tenant doesn't necessarily exist, which would be indicated by an initial reference returned by the statement above. Once the current tenant has been obtained by the URL \(in the example below for the type UI\) along with its different components, the currently active tenant can be obtained as follows:

> ### Sample Code:  
> ```abap
> " UI URL of the current tenant.
> DATA(lo_ui_url) = lo_current_tenant->get_url( xco_cp_tenant=>url_type->ui ).
>  
> " The protocol of the UI URL (Type string).
> DATA(lv_ui_url_protocol) = lo_ui_url->get_protocol( ).
>  
> " The host (including the domain) of the UI URL (Type string).
> DATA(lv_ui_url_host) = lo_ui_url->get_host( ).
>  
> " The port of the UI URL (Type i).
> DATA(lv_ui_url_port) = lo_ui_url->get_port( ).
> 
> ```

In a similar way it's also possible to access the information about the associated global account and subaccount:

> ### Sample Code:  
> ```abap
> " The string value of the global account ID of the current tenant.
> DATA(lv_global_account_id) = lo_current_tenant->get_global_account_id(
>   )->as_string( ).
> 
> " The string value of the subaccount ID of the current tenant.
> DATA(lv_subaccount_id) = lo_current_tenant->get_subaccount_id(
>   )->as_string( ).
> ```

