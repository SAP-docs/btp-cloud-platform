<!-- loiob958c17a762c437b98f9b7ac650d6f92 -->

# Batch and Change Set Request Instances

Find information about Client Proxy batch and change set request and the creation and use of a Client Proxy batch and change set request instance.



<a name="loiob958c17a762c437b98f9b7ac650d6f92__section_q3s_z52_rsb"/>

## OData V4 Batch Requests

A batch request allows the grouping of multiple individual requests into a single HTTP request payload.

The following individual requests in the context of a batch request exist:

-   Metadata Request

-   Data Request

-   Data Modification Request

-   Action Invocation Request

-   Function Invocation Request


Batch requests are submitted as a single `HTTP POST` request to the batch endpoint of a service located at the `$batch` URL related to the service root. Individual requests within a batch request are evaluated according to the same semantics used when the request appears outside the context of a batch request.

The same source states about change sets. In the *Multipart* format, data modification requests or action invocation requests may be grouped as part of an atomic change set. Operations outside the change set are executed sequentially, while operations within the change set can be executed in any order.

All requests in a change set represent a single change unit. Therefore, a batch request is a group of individual operations.

> ### Note:  
> In the context of batch requests, the term *operation* refers to an individual request in the batch request payload and must not be confused with the generalization of functions and actions. A change set request is a part of such a batch request.



<a name="loiob958c17a762c437b98f9b7ac650d6f92__section_uxd_5y2_rsb"/>

## Creating a Batch Request Instance

A batch request instance offers methods to add individual requests, executes the batch request, and checks the execution \(which is not to be confused with the execution of the individual operations – a batch request might be successful while one or more operations have failed\). The batch request instance then creates a change set request instance.

A batch request instance is created on the Client Proxy instance. For more information, see [Client Proxy Instance](client-proxy-instance-079517f.md).

Once you have created a batch request instance, define the operations, such as individual requests, and add them to the batch request or a change set, which is part of the batch request. The change set request instance is created directly on the batch request instance.



For more information on how to create and work with batch and change set requests, see [OData Request as Batch Including Changesets](odata-request-as-batch-including-changesets-fc10253.md)

