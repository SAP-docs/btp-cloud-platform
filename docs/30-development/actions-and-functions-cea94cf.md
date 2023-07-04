<!-- loiocea94cf65bed42b6b5796fbe7d980b51 -->

# Actions and Functions

Create an OData request to run an operation \(an action or function\) in the Client Proxy instance.



<a name="loiocea94cf65bed42b6b5796fbe7d980b51__section_d15_dtn_4tb"/>

## OData Version 2

See [\[MS-ODATA\]: Open Data Protocol \(OData\)](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-odata).



### Function

A Service Operation is represented by a Function Import and can return:

-   Primitive type

-   A single Entity-Type instance

-   A single Complex-Type instance

-   Collection of Complex-Type instances

-   Collection of Primitive types


The corresponding Function Import can have side effects and can be invoked by any pre-defined HTTP method.



<a name="loiocea94cf65bed42b6b5796fbe7d980b51__section_okj_ltn_4tb"/>

## OData Version 4

See [OData Version 4.01. Part 1: Protocol](https://docs.oasis-open.org/odata/odata/v4.01/odata-v4.01-part1-protocol.html).



### Function

**Functions** are operations exposed by an OData service that don't have side effects. Functions must return data and can include additional path segments. Functions are invoked using HTTP method `GET`.



### Action

 **Actions** are operation exposed by an OData service that can have side effects. Actions can return data but **must not** be composed with additional path segments. Actions are invoked using HTTP method `POST`.



### Operation

Functions and Actions are operations that can return data. Operations are either **bound** to a resource \(for example, an entity type\), that makes them members of that instance type. Operations can also be **unbound**. Unbound operations are called as static operations \(using “action imports” or “function imports”\) since a static \(unbound\) operation can't be called directly.



<a name="loiocea94cf65bed42b6b5796fbe7d980b51__section_p53_r5n_4tb"/>

## Example Requests



### Version 4 Function Import

“`GetEmployeeByManagerId`” with non-binding parameter “`ManagerId`”:

```
GET /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/GetEmployeeByManagerID(ManagerID='0001')
```



### V4 Bound Action

“`AcChangeTeamOfEmployee`” with non-binding parameter “`TeamId`”

```
POST /sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/EMPLOYEES('2')/SAP__self.AcChangeTeamOfEmployee
```

Request body:

```

{ 
"TeamID" : "TEAM_02" 
}
```



### Version 2 Function

“`SetEmployeeSalary`” with non-binding parameter “`Id`” and “`Amount`”

```
PUT /sap/opu/odata/IWBEP/TEA_TEST_APPLICATION/SetEmployeeSalary?Id='0001'&Amount=200
```

For examples and steps for Import and Bound operations, see:

-   [Import Operation](import-operation-8fce3ce.md)

-   [Bound Operation](bound-operation-6c29b98.md)




<a name="loiocea94cf65bed42b6b5796fbe7d980b51__section_on1_jfz_4tb"/>

## Constraints

-   If-Match header is only supported for **remote** consumption.

-   For function imports, the If-Match header is only supported for OData **Version 2** requests.

-   Composable Functions are **not** supported.

-   `$expand` with operations is `not` supported.

-   `$select` is `not` supported for actions.

-   `Return-Prefer` header is `not` supported for actions.

-   System query options are **not** supported for Version 4 functions.

-   If the return type of a Version 2 function is an entity type and this entity type is used by more than one entity set, the Version 2 request context only contains the \(EDM\) name of the first entity set with the underlying entity type. A precise mapping is currently not possible. For remote consumption, this can be handled in the proxy model by setting the correct entity set via method .`/iwbep/if_v4_med_func_imp->set_entity_set_name`


