<!-- loiocf072e85e14f42f5b7ab6cbfe7cf10a3 -->

# Content ID Referencing

You want to execute an OData $batch request using Content ID Referencing via the Client Proxy.



<a name="loiocf072e85e14f42f5b7ab6cbfe7cf10a3__section_jzs_gqg_ptb"/>

## OData Specification



### OData V2

See also: [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata)

Each MIME part representing a request in a Change Set MAY include a Content-ID MIME header, as specified in [\[RFC2045\]](https://www.rfc-editor.org/rfc/rfc2045.txt) section 7. If a MIME part defines an InsertEntity Request and includes a Content-ID header, then the new entity, defined by the InsertEntity Request, MAY be referenced by subsequent requests in the Change Set by using the "$<Content-ID value of previous request\>" token in place of a Resource Path identifying the new resource. When used in this way, the token acts as an alias for the Resource Path that identifies the new entity. Requests in different Change Sets cannot reference one another, even if they are in the same Batch.



### OData V4

See also: [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html)

Each individual request within a batch request MAY have a request identifier assigned. The request identifier is case-sensitive, MUST be unique within the batch request, and MUST satisfy the rule request-id in [\[OData-ABNF\]](https://docs.oasis-open.org/odata/odata/v4.01/os/abnf/odata-abnf-construction-rules.txt).

The contents of a body part representing a change set MUST itself be a multipart document \(see [\[RFC2046\]](https://datatracker.ietf.org/doc/html/rfc2046)\) with one body part for each operation in the change set. Each body part representing an operation in the change set MUST specify a Content-ID header with a request identifier that is unique within the batch request.



<a name="loiocf072e85e14f42f5b7ab6cbfe7cf10a3__section_j5k_grg_ptb"/>

## Example Requests



### V4

Create new entity in entity set “TEAMS” and update it afterwards:

```
POST /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/$batch
```

```


With request body

--batch 
content-type: multipart/mixed; boundary=changeset

--changeset 
content-type: application/http 
content-id: 111 

POST TEAMS HTTP/1.1
Content-Type: application/json

{ 
"Name":"Unit Test Task Force", 
"MANAGER_ID":"3",
"BudgetCurrency":"JPY",
"Budget":111100 
}

--changeset
content-type: application/http
content-id: 222 

PATCH $111 HTTP/1.1
Content-Type: application/json

{ 
"MEMBER_COUNT":66 
} 

--changeset--
--batch—


```



### V2

Create a new entity in entity set “Decimals” and read it afterwards:

```
POST /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/$batch
```

```


With request body

--batch 
Content-Type: multipart/mixed; boundary=changeset

--changeset 
Content-Type: application/http
Content-Transfer-Encoding: binary

POST Decimals HTTP/1.1 
Content-Type: application/json 
Accept: application/json 
Content-Id: 1

{
 "Id" : 1,
 "Name" : "Decimal 10",
 "Decimal1" : "1.1000000000" 
} 

--changeset---

--batch 

Content-Type: application/http
Content-Transfer-Encoding: binary 
Accept: application/json

GET $1?$format=json HTTP/1.1 


--batch--
```



<a name="loiocf072e85e14f42f5b7ab6cbfe7cf10a3__section_x1j_gkh_ptb"/>

## How-to



### Overview

> ### Note:  
> As the coding itself is independent of the OData version, we will just present one general example on how to use Content ID Referencing.

Starting point for a using Content ID Referencing is a create request instance. There, it is possible to create an entity resource with a Content ID reference.



### Example

You want to create a new entity in entity set “Teams” and update the member count afterwards:

```
POST /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/$batch
```

```


With request body

--batch
content-type: multipart/mixed; boundary=changeset

--changeset 
content-type: application/http
content-id: 111

POST Teams HTTP/1.1
Content-Type: application/json

{
"Name":"Unit Test Task Force"
}
--changeset
content-type: application/http
content-id: 222

PATCH $111 HTTP/1.1
Content-Type: application/json

{ 
"MemberCount":42 
} 

--changeset-- 
--batch--


 DATA: lo_create_request         TYPE REF TO /iwbep/if_cp_request_create,

        lo_batch_request         TYPE REF TO /iwbep/if_cp_request_batch,

        lo_changeset_request     TYPE REF TO /iwbep/if_cp_request_changeset,

        lo_update_request        TYPE REF TO /iwbep/if_cp_request_update,

        lo_entity_resource_w_cir TYPE REF TO /iwbep/if_cp_resource_entity,

        ls_patch_data            TYPE /iwbep/s_v4_tea_team.


  lo_entity_resource_w_cir = lo_create_request->create_res_w_content_id_ref( ).


  lo_update_request = lo_entity_resource_w_cir->create_request_for_update( /iwbep/if_cp_request_update=>gcs_update_semantic-patch ).

  ls_patch_data = VALUE #( member_count = 42 ).

  lo_update_request->set_business_data( is_business_data = ls_patch_data

                     It_provided_property = VALUE #( ( `MEMBER_COUNT` ) ) ).


  lo_changeset_request->add_request( lo_create_request ).

  lo_changeset_request->add_request( lo_update_request ).

  lo_batch_request->add_request( lo_changeset_request ).

  lo_batch_request->execute( ).
```



### Step-by-step

**Step 1:** You create the entity resource with a Content ID reference at the create request instance:

```


  DATA: lo_create_request TYPE REF TO /iwbep/if_cp_request_create,
	    lo_entity_resource_w_cir TYPE REF TO /iwbep/if_cp_resource_entity.
 
  lo_entity_resource_w_cir = lo_create_request->create_res_w_content_id_ref( ).
```

> ### Note:  
> See the corresponding chapter to learn how to build a create request instance.

**Step 2:** Now you create the update request instance at the entity resource instance:

```


  DATA: lo_update_request TYPE REF TO /iwbep/if_cp_request_update,
	   lo_entity_resource_w_cir TYPE REF TO /iwbep/if_cp_resource_entity.
 
  lo_update_request = lo_entity_resource_w_cir->create_request_for_update( /iwbep/if_cp_request_update=>gcs_update_semantic-patch ).
```

> ### Note:  
> See the corresponding chapter for more details on update requests.

**Step 3:** Define the corresponding update data and set it into the update request:

```


  DATA: lo_update_request TYPE REF TO /iwbep/if_cp_request_update,

	   ls_patch_data TYPE /iwbep/s_v4_tea_team.


  ls_patch_data = value #( member_count = 42 ).

  lo_update_request->set_business_data( is_business_data = ls_patch_data
								 It_provided_property = VALUE #( ( `MEMBER_COUNT` ) ) ).
```

> ### Note:  
> See the corresponding chapter for more details on update requests.

**Step 4:** Add both the CREATE as well as the UPDATE request into the changeset request; then, add the changeset request into the $batch request:

```

  DATA: lo_create_request    TYPE REF TO /iwbep/if_cp_request_create,

        lo_batch_request     TYPE REF TO /iwbep/if_cp_request_batch,

        lo_changeset_request TYPE REF TO /iwbep/if_cp_request_changeset,

        lo_update_request    TYPE REF TO /iwbep/if_cp_request_update.

  lo_changeset_request->add_request( lo_create_request ).

  lo_changeset_request->add_request( lo_update_request ).

  lo_batch_request->add_request( lo_changeset_request ).

```

> ### Note:  
> See the corresponding chapter on how to create a changeset/$batch request instance.

**Step 5:**Execute the $batch request:

```


  DATA: lo_batch_request TYPE REF TO /iwbep/if_cp_request_batch.

  lo_batch_request->execute( ).
```

> ### Note:  
> See the corresponding chapter for a detailed description on how to handle $batch requests and how to fetch the business data after successful request execution.



<a name="loiocf072e85e14f42f5b7ab6cbfe7cf10a3__section_eyj_tph_ptb"/>

## Constraints

-   Content ID Referencing is not supported in combination with navigation \(e.g. POST $1/NavigationProperty\)


