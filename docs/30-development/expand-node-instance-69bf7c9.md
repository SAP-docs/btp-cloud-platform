<!-- loio69bf7c94f2e043f6bfa860e7de641afa -->

# Expand Node Instance

An expand node instance causes related entities to be included inline in the response.



<a name="loio69bf7c94f2e043f6bfa860e7de641afa__section_wtb_qsm_4tb"/>

## Overview

When reading an entity with a `GET` request, related entities can also be requested using the `$expand` statement on a navigation property. In this example, you want to read the data about customer “Posey” and the open sales orders for this customer \(with navigation property “***Customer\_2\_Salesorders***”\). Here is an example of this OData request:

> ### Sample Code:  
> ```
> GET http://host/service/Customers(‘Posey’)?$expand=Customer_2_Salesorders
> ```



<a name="loio69bf7c94f2e043f6bfa860e7de641afa__section_u44_qsm_4tb"/>

## Creating an Instance

In the Client Proxy Framework, an expand expression is described by an expand node instance. It is created directly in the corresponding read request instance.

> ### Note:  
> In OData Version 2, complex properties can't have associations, such as navigation properties. You can only define navigation properties in entity types. In OData Version 4, you can define navigation properties for a complex property.

An expand node instance is always created in the corresponding [Request Instance](request-instance-7bda471.md). These request types can be used to create an expand node:

-   read entity

-   read entity list

-   read entity zero-to-one




<a name="loio69bf7c94f2e043f6bfa860e7de641afa__section_ucc_ssm_4tb"/>

## Functionality

The expand node instances add an expand expression into the underlying read request. You can also set the selected properties for each expand node. If not all properties of the expanded entity are returned, compare to ***GET http://host/service/Customers\(‘Posey’\)?$expand=Customer\_2\_Salesorders\($select=Date,Status\)***.



<a name="loio69bf7c94f2e043f6bfa860e7de641afa__section_pjw_pvm_4tb"/>

## Example

For examples of how to create and work with expand nodes, see [$expand Option](expand-option-215cca8.md).

**Related Information**  


[Request Instance](request-instance-7bda471.md "A request instance describes the action you want to take on a resource.")

