<!-- loio03bc28091f0d4d6790d45fdbd1e2fbad -->

# Deep Create \(Data Description Node\)

In this chapter, we will learn the meaning of a Client Proxy Data Description node as well as how to create and use a Client Proxy Data Description node instance which describes the format of request business data and is therefore needed to perform a deep create.



<a name="loio03bc28091f0d4d6790d45fdbd1e2fbad__section_b4c_czm_4tb"/>

## Overview

The OData V4 spec defines a `“deep create”` \(aka “deep insert”\) as “a request to create an entity that includes related entities, represented using the appropriate inline representation”.

Consider the following example: You want to create a new customer including the first sales order from him. You could either first create the new customer and – as next step – the first sales order or you can – using a deep create – create both at the same time:

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

To describe the properties and inlined navigations of the \(deep\) business data for such a request in the context of the Client Proxy, you must use a Data Description node. Plainly speaking, that means that a Data Description node is needed in order to describe the structure of your deep business data to the Client Proxy.

A Data Description node is always created on the underlying create [Request Instance](request-instance-7bda471.md).

> ### Note:  
> According to the V2 specification \(version June 10, 2011\) complex properties cannot have associations, i.e. they cannot have navigation properties; navigation properties can be only defined in entity types. In OData V4, a complex property can also have navigation properties defined.



<a name="loio03bc28091f0d4d6790d45fdbd1e2fbad__section_osh_dzm_4tb"/>

## Creating an Instance

A Data Description node instance is always created on the underlying create [Request Instance](request-instance-7bda471.md).



<a name="loio03bc28091f0d4d6790d45fdbd1e2fbad__section_us5_dzm_4tb"/>

## Functionality

The main functionality of Data Description node instances is to describe the \(possibly partial\) payload for a deep create request to the Client Proxy. It is therefore mandatory in order to execute any deep create request.



<a name="loio03bc28091f0d4d6790d45fdbd1e2fbad__section_byw_2zm_4tb"/>

## Example

Examples on how to create and work with Data Description nodes are given in [OData Request: Deep Create](odata-request-deep-create-c892396.md).

