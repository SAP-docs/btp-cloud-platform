<!-- loiod0e97ff5680841aabef2a9d77359427b -->

# Filter Node Instance

A filter node instance filters and returns only the results that match the specified expressions.



<a name="loiod0e97ff5680841aabef2a9d77359427b__section_b4c_czm_4tb"/>

## Overview

The ***$filter*** system query option restricts the set of items returned. It allows you to filter are source collection addressed by a request URI. The expression specified with ***$filter*** is evaluated for each resource in the collection. Only items where the expression is ***true*** are included in the response.

In this example, you want to read a collection of sales orders and get only the unpaid orders. Here's an example of the OData request:

> ### Sample Code:  
> ```
> GET http://host/service/SalesOrders?$filter=Payment eq ‘open’
> ```

A filter expression is described by a filter node instance that a filter factory instance creates and can be set into the Client Proxy instance.

> ### Note:  
> The filter nodes are not OData protocol-specific \(Version 2 or Version 4\).



<a name="loiod0e97ff5680841aabef2a9d77359427b__section_osh_dzm_4tb"/>

## Creating an Instance

A filter node instance is always created by a filter factory instance. You can create a filter factory instance in a read list request instance.



<a name="loiod0e97ff5680841aabef2a9d77359427b__section_us5_dzm_4tb"/>

## Functionality

The main functionality of filter node instances is to create a filter expression for a read request on an entity list, which can be integrated into the corresponding request to only show a subset of the complete result.



<a name="loiod0e97ff5680841aabef2a9d77359427b__section_byw_2zm_4tb"/>

## Example

For examples of how to create and work with filter nodes, see [$filter Option](filter-option-dfe8bfc.md).

**Related Information**  


[OData Request: Read Entity](odata-request-read-entity-9d7dde4.md "To create an OData request to read an entity in the Client Proxy instance.")

