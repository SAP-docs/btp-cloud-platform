<!-- loiofc1025313d534d2a95afc6b117e85d1d -->

# OData Request as Batch Including Changesets

You want to execute an OData request as $batch including changesets using the Client Proxy.



<a name="loiofc1025313d534d2a95afc6b117e85d1d__section_wqh_4jz_4tb"/>

## OData Specification



### OData V2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata)

\(…\) use cases exist where it is beneficial to enable a client of a data service to "batch" up a group of requests and send that Batch to the data service in a single HTTP request. This section defines a Batch Request type which reduces the number of roundtrips to a data service for applications that need to make numerous requests and a ChangeSet syntax as a way to logically group a set of requests into a single unit within a batch.



### OData V4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html)

Batch requests allow grouping multiple individual requests into a single HTTP request payload. An individual request in the context of a batch request is a Metadata Request, Data Request, Data Modification Request, Action invocation request, or Function invocation request.

Batch requests are submitted as a single HTTP POST request to the batch endpoint of a service, located at the URL $batch relative to the service root.

Individual requests within a batch request are evaluated according to the same semantics used when the request appears outside the context of a batch request.

In the Multipart format, data modification requests or action invocation requests may be grouped as part of an atomic change set. Operations outside the change set are executed sequentially, while operations within the change set may be executed in any order.



<a name="loiofc1025313d534d2a95afc6b117e85d1d__section_ehd_dvz_4tb"/>

## Example Requests



### V4

Get all entities of entity set “EMPLOYEES” with Id = ‘1’ and execute the Action Import “ChangeTeamBudgetByID”:

```
POST /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/$batch
```

```

With request body

--batch
Content-Type: application/http
Content-Transfer-Encoding: binary
GET EMPLOYEES?$filter=ID%20eq%20%271%27 HTTP/1.1

--batch 
Content-Type: multipart/mixed;boundary=change_set_1

--change_set_1 
Content-Type: application/http

Content-Transfer-Encoding: binary
Content-ID: 1 

POST ChangeTeamBudgetByID HTTP/1.1
Content-Type: application/json
{
	"TeamID" : "TEAM_01",
	"Budget" : 700.00
 } 
--change_set_1-- 
--batch--
```



### V2

Update two entities of entity set ‘Conversions’

```
POST /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/$batch
```

```


With request body

--batch
Content-Type: multipart/mixed; boundary=changeset

--changeset Content-Type: application/http
Content-Transfer-Encoding: binary

PUT Conversions(Id='0001') HTTP/1.1
Content-Type: application/json 

{ 
	"Id" : "1",
	"price_1" : "-180.59", 
	"currency_1" : "EUR", 
	"price_2" : "1.706", 
	"currency_2" : "KWD", 
	"amount_1" : "1.1235", 
	"unit_1" : "D",
	"amount_2" : "1.123",
	"unit_2" : "CMS",
	"oSQL_Where_Cl" : "",
	"Is_Boolean" : true
	 } 

--changeset--

--batch 
Content-Type: multipart/mixed; boundary=changeset

--changeset 
Content-Type: application/http 
Content-Transfer-Encoding: binary

PUT Conversions(Id='0001') HTTP/1.1 
Content-Type: application/json 

{ 
		"Id" : "1", 
		"price_1" : "-000.00",
		"currency_1" : "EUR", 
		"price_2" : "1.706",
		"currency_2" : "KWD", 
		"amount_1" : "1.1235",
		"unit_1" : "D",
		"amount_2" : "1.123",
		"unit_2" : "CMS",
		"oSQL_Where_Cl" : "",
		"Is_Boolean" : true
		}

--changeset--
--batch--
```



<a name="loiofc1025313d534d2a95afc6b117e85d1d__section_zf3_rcg_ptb"/>

## How-To



### Overview

**Note:** As the coding itself is independent of the OData version, we will just present one general example on how to create a $batch request including changesets.

Starting point for a $batch request is the Client Proxy instance. There, it is possible to create a $batch request, which can then be used to create a changeset request.



### Example

You want to get all entities of entity set “Employees” and create a new entity in entity set “Teams”:

```
POST /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/$batch
```

```


With request body

--batch
Content-Type: application/http
Content-Transfer-Encoding: binary

GET Employees HTTP/1.1 


--batch 
Content-Type: multipart/mixed;boundary=change_set_1

--change_set_1
Content-Type: application/http
Content-Transfer-Encoding: binary
Content-ID: 1

POST Teams HTTP/1.1
Content-Type: application/json

{ 
		"Id" : "TEAM_04", 
		"Name" : "Test Team" 
} 

--change_set_1-- 
--batch--

  DATA: lo_client_proxy      TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_read_request      TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_read_response     TYPE REF TO /iwbep/if_cp_response_read_lst,
        lo_create_request    TYPE REF TO /iwbep/if_cp_request_create,
        lo_create_response   TYPE REF TO /iwbep/if_cp_response_create,
        lo_batch_request     TYPE REF TO /iwbep/if_cp_request_batch,
        lo_changeset_request TYPE REF TO /iwbep/if_cp_request_changeset,
        lt_employee          TYPE STANDARD TABLE OF /iwbep/s_v4_tea_employee,
        ls_team              TYPE /iwbep/s_v4_tea_team.


  lo_batch_request = lo_client_proxy->create_request_for_batch( ).

  lo_changeset_request = lo_batch_request->create_request_for_changeset( ).
  lo_changeset_request->add_request( lo_create_request ).
  
  lo_batch_request->add_request( lo_read_request ).
  lo_batch_request->add_request( lo_changeset_request ).
  lo_batch_request->execute( ).


  lo_batch_request->check_execution( ).
  lo_changeset_request->check_excecution( ).
  lo_read_request->check_execution( ).
  lo_create_request->check_execution( ).

  lo_read_response = lo_read_request->get_response( ).
  lo_read_response->get_business_data( IMPORTING et_business_data = lt_employee ).
  
  lo_create_response = lo_create_request->get_response( ).
  lo_create_response->get_business_data( IMPORTING es_business_data = ls_team ).
```



### Step-by-step

**Step 1:** You create the $batch request at the client proxy instance:

```

  DATA: lo_client_proxy  TYPE REF TO /iwbep/if_cp_client_proxy,
        lo_batch_request TYPE REF TO /iwbep/if_cp_request_batch.

  lo_batch_request = lo_client_proxy->create_request_for_batch( ).
```

**Step 2:** Now you create the changeset request using the $batch request instance:

```

  DATA: lo_batch_request     TYPE REF TO /iwbep/if_cp_request_batch,
        lo_changeset_request TYPE REF TO /iwbep/if_cp_request_changeset.

  lo_changeset_request = lo_batch_request->create_request_for_changeset( ).
```

**Step 3:** You add the CREATE request into the changeset request:

```

  DATA: lo_create_request    TYPE REF TO /iwbep/if_cp_request_create,
        lo_changeset_request TYPE REF TO /iwbep/if_cp_request_changeset.

  lo_changeset_request->add_request( lo_create_request ).
```

> ### Note:  
> See the corresponding chapter on how to create a CREATE entity request.

**Step 4:** Add both the READ as well as the changeset request into the $batch request; then, execute the $batch request:

```

  DATA: lo_read_request      TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_batch_request     TYPE REF TO /iwbep/if_cp_request_batch,
        lo_changeset_request TYPE REF TO /iwbep/if_cp_request_changeset.

  lo_batch_request->add_request( lo_read_request ).
  lo_batch_request->add_request( lo_changeset_request ).
  lo_batch_request->execute( ).

```

> ### Note:  
> See the corresponding chapter on how to create a READ entity list request.

**Step 5:** Check the 4 requests for successful execution \(this step is optional\):

```

  DATA: lo_read_request      TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_create_request    TYPE REF TO /iwbep/if_cp_request_create,
        lo_batch_request     TYPE REF TO /iwbep/if_cp_request_batch,
        lo_changeset_request TYPE REF TO /iwbep/if_cp_request_changeset.


  lo_batch_request->check_execution( ).
  lo_changeset_request->check_excecution( ).
  lo_read_request->check_execution( ).
  lo_create_request->check_execution( ).

```

> ### Note:  
> If the exception was unsuccessful, CHECK\_EXECUTION will raise an exception. See the corresponding chapter about execution handling on how to properly react in such a case.

**Step 6:** Get the READ response instance via the READ request instance and use it to fetch the corresponding business data:

```

  DATA: lo_read_request  TYPE REF TO /iwbep/if_cp_request_read_list,
        lo_read_response TYPE REF TO /iwbep/if_cp_response_read_lst,
        lt_employee      TYPE STANDARD TABLE OF /iwbep/s_v4_tea_employee.

  lo_read_response = lo_read_request->get_response( ).
  lo_read_response->get_business_data( IMPORTING et_business_data = lt_employee ).
```

**Step 7:** Get the CREATE response instance via the CREATE request instance and use it to fetch the corresponding business data:

```

  DATA: lo_create_request  TYPE REF TO /iwbep/if_cp_request_create,
        lo_create_response TYPE REF TO /iwbep/if_cp_response_create,
        ls_team            TYPE /iwbep/s_v4_tea_team.

  lo_create_response = lo_create_request->get_response( ).
  lo_create_response->get_business_data( IMPORTING es_business_data = ls_team ).
```

