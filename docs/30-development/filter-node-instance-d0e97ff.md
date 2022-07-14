<!-- loiod0e97ff5680841aabef2a9d77359427b -->

# Filter Node Instance

In this chapter, we will learn the meaning of a Client Proxy filter node as well as how to create and use a Client Proxy filter node instance.



<a name="loiod0e97ff5680841aabef2a9d77359427b__section_b4c_czm_4tb"/>

## Overview

The $filter system query option restricts the set of items returned. It allows clients to filter a collection of resources that are addressed by a request URI; the expression specified with $filter is evaluated for each resource in the collection, and only items where the expression evaluates to true are included in the response.

Consider the following example: You want to read a collection of sales orders and only get the ones not paid yet. This translates to the following as an example OData request

> ### Sample Code:  
> ```
> GET http://host/service/SalesOrders?$filter=Payment eq ‘open’
> ```

Within the Client Proxy Framework, a filter expression is described by a filter node instance, which is created by a filter factory instance and can be set into the [Client Proxy Instance](client-proxy-instance-079517f.md)-

> ### Note:  
> The filter nodes are not OData protocol \(V2 or V4\) specific.



<a name="loiod0e97ff5680841aabef2a9d77359427b__section_osh_dzm_4tb"/>

## Creating an Instance

A filter node instance is always created by a filter factory instance. A filter factory instance can be created at a read list request instance. For more information, see [Request Instance](request-instance-7bda471.md).



<a name="loiod0e97ff5680841aabef2a9d77359427b__section_us5_dzm_4tb"/>

## Functionality

The main functionality of filter node instances is to create a filter expression for a read request on an entity list, which can be integrated into the corresponding request to only show a subset of the complete result.



<a name="loiod0e97ff5680841aabef2a9d77359427b__section_byw_2zm_4tb"/>

## Example

Examples on how to create and work with filter nodes are given in the corresponding How-To section [OData Request: System Query Option $filter](odata-request-system-query-option-filter-dfe8bfc.md).

