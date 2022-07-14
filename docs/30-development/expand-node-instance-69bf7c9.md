<!-- loio69bf7c94f2e043f6bfa860e7de641afa -->

# Expand Node Instance

In this chapter, we will learn the meaning of a Client Proxy expand node as well as how to create and use a Client Proxy expand node instance.



<a name="loio69bf7c94f2e043f6bfa860e7de641afa__section_wtb_qsm_4tb"/>

## Overview

The`$expand` system query option indicates the related entities and stream values that must be represented inline. Therefore, when reading an entity with a `GET` request, related entities can be requested as well by using the `$expand` statement on a navigation property.

Consider this example: You want to read the data about customer “Alf” and also see his open sales orders \(via navigation property “Customer\_2\_Salesorders”\). This translates to the the following OData example request:

> ### Sample Code:  
> ```
> GET http://host/service/Customers(‘Alf’)?$expand=Customer_2_Salesorders
> ```



<a name="loio69bf7c94f2e043f6bfa860e7de641afa__section_u44_qsm_4tb"/>

## Creating an Instance

Within the Client Proxy Framework, an expand expression is described by an expand node instance, which is created directly at the corresponding read request instance.

For more details, see [Request Instance](request-instance-7bda471.md).

> ### Note:  
> According to the V2 specification \(version June 10, 2011\) complex properties cannot have associations, i.e. they cannot have navigation properties. In this case, navigation properties can be only defined in entity types. In OData V4, a complex property can also have navigation properties defined.

An expand node instance is always created on the corresponding [Request Instance](request-instance-7bda471.md). The following request kinds can create an expand node:

-   read entity

-   read entity list

-   read entity zero-to-one




<a name="loio69bf7c94f2e043f6bfa860e7de641afa__section_ucc_ssm_4tb"/>

## Functionality

The main functionality of expand node instances is to add an expand expression into the underlying read request. Furthermore, it is also possible to set the selected properties of each expand node \(in case not all properties of the expanded entity shall be returned; compare to GET http://host/service/Customers\(‘Alf’\)?$expand=Customer\_2\_Salesorders\($select=Date,Status\)\).



<a name="loio69bf7c94f2e043f6bfa860e7de641afa__section_pjw_pvm_4tb"/>

## Example

Examples on how to create and work with expand nodes are given in the corresponding How-To section in [OData Request: System Query Option $expand](odata-request-system-query-option-expand-215cca8.md).

