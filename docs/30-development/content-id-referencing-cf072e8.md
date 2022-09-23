<!-- loiocf072e85e14f42f5b7ab6cbfe7cf10a3 -->

# Content ID Referencing

Create an OData $batch request using Content ID Referencing in the Client Proxy instance.



<a name="loiocf072e85e14f42f5b7ab6cbfe7cf10a3__section_jzs_gqg_ptb"/>

## OData Specification



### OData Version 2

See [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata).

Multipurpose Internet Mail Extensions \(MIME\) is set of extensions that redefines and expands support for various types of content in email messages. Each MIME part that represents a request in a Change Set can include a Content-ID MIME header. See [\[RFC2045 Section 7: Content-ID Header Field\]](https://www.rfc-editor.org/rfc/rfc2045.txt) for more information.

If a MIME part defines an ***InsertEntity*** request and includes a ***Content-ID*** header, the new entity is defined by the ***InsertEntity*** request. You can reference the new entity in future requests in the Change Set using the "***$<Content-ID value of your previous request\>***" token in place of a Resource Path that identifies the new resource. The token acts as an alias for the Resource Path that identifies the new entity. Requests in different Change Sets can't reference one another, even if they are in the same Batch.



### OData Version 4

See [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html).

Each request in a batch request can have an assigned request identifier. The request identifier:

-   is case-sensitive.
-   Must be unique within the batch request.
-   Must satisfy the rule request-id in [\[OData-ABNF\]](https://docs.oasis-open.org/odata/odata/v4.01/os/abnf/odata-abnf-construction-rules.txt).

The body part contents that represent a change set must be a multipart document with one body part for each operation in the change set. See [\[RFC2046\]](https://datatracker.ietf.org/doc/html/rfc2046). Each body part that represents an operation in the change set must specify a ***Content-ID*** header with a unique request identifier in the batch request.



<a name="loiocf072e85e14f42f5b7ab6cbfe7cf10a3__section_j5k_grg_ptb"/>

## Example Requests



### Version 4

Create new entity in entity set “***TEAMS***” and update it afterwards:

```
POST /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/$batch
```

With request body

```
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



### Version 2

Create a new entity in entity set “***Decimals***”, then read it:

```
POST /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/$batch
```

With request body

```
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

## Create a $batch request using Content ID Referencing



### Overview

> ### Note:  
> As the coding is independent of the OData version, we're presenting a general example on how to create an OData $batch request using Content ID Referencing.

The starting point for a using Content ID Referencing is a create request instance and create an entity resource with a Content ID reference.



### Example

Create a new entity in entity set “***Teams***”, then update the member count:

```
POST /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0003/$batch
```

With request body

```
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



```

```
DATA:	lo_create_request        TYPE REF TO /iwbep/if_cp_request_create,
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



### Steps

**Step 1:** Create the entity resource with a Content ID reference in the create request instance:

```
DATA:	lo_create_request TYPE REF TO /iwbep/if_cp_request_create,
	     lo_entity_resource_w_cir TYPE REF TO /iwbep/if_cp_resource_entity.
		 lo_entity_resource_w_cir = lo_create_request->create_res_w_content_id_ref( ).
```

**Step 2:** Create the update request instance at the entity resource instance:

```
DATA:    lo_update_request TYPE REF TO /iwbep/if_cp_request_update,
		 lo_entity_resource_w_cir TYPE REF TO /iwbep/if_cp_resource_entity.
		 lo_update_request = lo_entity_resource_w_cir->create_request_for_update( /iwbep/if_cp_request_update=>gcs_update_semantic-patch ).
```

**Step 3:** Define the corresponding update data and set it into the update request:

```
DATA:    lo_update_request TYPE REF TO /iwbep/if_cp_request_update,
		 ls_patch_data TYPE /iwbep/s_v4_tea_team.
		 ls_patch_data = value #( member_count = 42 ).
		 lo_update_request->set_business_data( is_business_data = ls_patch_data
		  
		 It_provided_property = VALUE #( ( `MEMBER_COUNT` ) ) ).
```

**Step 4:**Add the ***CREATE*** and ***UPDATE*** requests into the changeset request. Then add the changeset request into the ***$batch*** request:

```
DATA:	lo_create_request        TYPE REF TO /iwbep/if_cp_request_create,
         lo_batch_request         TYPE REF TO /iwbep/if_cp_request_batch,
         lo_changeset_request 	TYPE REF TO /iwbep/if_cp_request_changeset,
		 lo_update_request   	 TYPE REF TO /iwbep/if_cp_request_update.
	
		 lo_changeset_request->add_request( lo_create_request ).
		 lo_changeset_request->add_request( lo_update_request ).
		 lo_batch_request->add_request( lo_changeset_request ).

```

**Step 5:**Run the ***$batch*** request:

```
DATA:	lo_batch_request TYPE REF TO /iwbep/if_cp_request_batch.
		 lo_batch_request->execute( ).
```



<a name="loiocf072e85e14f42f5b7ab6cbfe7cf10a3__section_eyj_tph_ptb"/>

## Constraints

-   You can't use Content ID Referencing with navigation \(for example, ***POST $1/NavigationProperty***\).


**Related Information**  


[Request Instance](request-instance-7bda471.md "A request instance describes the action you want to take on a resource.")

[Resource Instance](resource-instance-25e2e3d.md "A resource instance represents a resource that is shared between applications and identified using URLs and defined in the data model.")

[OData Request as Batch Including Changesets](odata-request-as-batch-including-changesets-fc10253.md "Create an $batch request, including changesets in the Client Proxy instance.")

