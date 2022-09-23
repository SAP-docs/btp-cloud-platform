<!-- loio03bc28091f0d4d6790d45fdbd1e2fbad -->

# Deep Create Data Description Node

In OData Version 4, deep create requests create an entity that includes related entities.



<a name="loio03bc28091f0d4d6790d45fdbd1e2fbad__section_b4c_czm_4tb"/>

## Overview

A ***deep create*** is also known as ***deep insert***\). In this example, you want to create a new customer and the first sales order from this customer. You can first create the new customer and then the first sales order or you can use a ***deep create*** to create both at the same time:

```
POST http://host/service/Customers
```

This request contains the following payload:

```
{ "CustomerName" : "James Bond",
          "CustomerId" : 007, 
          "Customer_2_Salesorders" : { 
                       "Object" : "Walther PPK", 
                       "Category" : "Pistols" 
                                      }
         }
```

You must use a Data Description node to describe the properties and inline navigations for deep business data for a request. The Data Description node is necessary to describe the structure of your deep business data to the Client Proxy.

A Data Description node is always created on the corresponding create [Request Instance](request-instance-7bda471.md).

> ### Note:  
> In OData Version 2, complex properties can't have associations, such as navigation properties. You can only define navigation properties in entity types. In OData Version 4, you can define navigation properties for a complex property.



<a name="loio03bc28091f0d4d6790d45fdbd1e2fbad__section_osh_dzm_4tb"/>

## Creating an Instance

A Data Description node instance is always created in the corresponding [Request Instance](request-instance-7bda471.md).



<a name="loio03bc28091f0d4d6790d45fdbd1e2fbad__section_us5_dzm_4tb"/>

## Functionality

The Data Description node instances describe the payload for a deep create request to the Client Proxy. This is required to execute any deep create request.



<a name="loio03bc28091f0d4d6790d45fdbd1e2fbad__section_byw_2zm_4tb"/>

## Example

For examples of how to create and work with Data Description nodes, see [OData Request: Deep Create](odata-request-deep-create-c892396.md).

**Related Information**  


[OData Request: Deep Create](odata-request-deep-create-c892396.md "Create an OData request to execute a “deep create” (deep insert) in the Client Proxy instance.")

