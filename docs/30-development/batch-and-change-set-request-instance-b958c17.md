<!-- loiob958c17a762c437b98f9b7ac650d6f92 -->

# Batch and Change Set Request Instance

Batch requests group multiple individual requests into a single HTTP request payload.



<a name="loiob958c17a762c437b98f9b7ac650d6f92__section_q3s_z52_rsb"/>

## OData Version 4 Batch Requests

These individual requests can be included in a batch request:

-   Metadata

-   Data

-   Data Modification

-   Action Invocation

-   Function Invocation


Batch requests are submitted as a single `HTTP POST` request to the batch endpoint of a service at the ***$batch*** URL that is related to the service root. Individual requests in a batch request are evaluated according to the same semantics used with an individual request.

In the *Multipart* format, you can group data modification requests or action invocation requests as part of an atomic change set. Operations outside the change set are executed sequentially. Operations in the change set are executed in any order.

> ### Note:  
> In batch requests, *operation* is an individual request in the batch request payload. A change set request is a part of this type of batch request.



<a name="loiob958c17a762c437b98f9b7ac650d6f92__section_uxd_5y2_rsb"/>

## Creating a Batch Request Instance

A batch request instance is created on the Client Proxy instance. It adds individual requests, executes the batch request, and checks the execution. The batch request instance creates a change set request instance.

After you create a batch request instance, you can define the operations and add them to the batch request or to a change set. The change set request instance is created directly on the batch request instance.

**Related Information**  


[OData Client Proxy Tasks](odata-client-proxy-tasks-2ad7bcc.md "Get an overview of some of the most common OData Client Proxy tasks.")

[OData Request as Batch Including Changesets](odata-request-as-batch-including-changesets-fc10253.md "Create an $batch request, including changesets in the Client Proxy instance.")

