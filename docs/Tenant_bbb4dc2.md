<!-- loiobbb4dc2e1ed240e98a20fc73705fc46f -->

# Tenant

The XCO tenant module provides standard abstractions for querying information about tenants, in particular the tenant associated with the current ABAP session. The central abstraction is IF\_XCO\_CP\_TENANT which represents a tenant and is used to retrieve its public information. As of now, the following information can be retrieved

-   ID: The ID for the tenant

-   GUID: The GUID for the tenant \(represented as an IF\_XCO\_UUID\)

-   URL: The URL of the tenant for the given URL type \(URL types are available via XCO\_CP\_TENANT=\>URL\_TYPE\)


To obtain the object for the currently active tenant and query its UI URL the following code can be used:

```lang-abap
DATA(lo_current_tenant) = xco_cp=>current->tenant( ).
 
 " UI URL of the current tenant.
DATA(lo_ui_url) = lo_current_tenant->get_url( xco_cp_tenant=>url_type->ui ).
 
" The protocol of the UI URL (Type string).
DATA(lv_ui_url_protocol) = lo_ui_url->get_protocol( ).
 
" The host (including the domain) of the UI URL (Type string).
DATA(lv_ui_url_host) = lo_ui_url->get_host( ).
 
" The port of the UI URL (Type i).
DATA(lv_ui_url_port) = lo_ui_url->get_port( ).

```

