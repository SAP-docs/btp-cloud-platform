<!-- loio6ab460e1a59e4890b8faa3fcc35f3343 -->

# Enable SOAP Communication in Your ABAP Code

SOAP-based Web service outbound communication within the ABAP environment is enabled by using SOAP destination objects.



<a name="loio6ab460e1a59e4890b8faa3fcc35f3343__section_tbk_413_zkb"/>

## Context

A SOAP destination is used to instantiate the Web service consumer proxy in the coding. You have the following options to create a SOAP destination object:

-   Communication arrangement approach: By specifying a destination based on a communication arrangement. See [Communication Arrangement](communication-arrangement-201de48.md).
-   Destination service approach: By using a destination that is maintained in a destination service that resides in the Cloud Foundry environment \(not relevant for Developer Extensibility, see [Developer Extensibility](https://help.sap.com/viewer/6aa39f1ac05441e5a23f484f31e477e7/latest/en-US/e1059ff581854a699f15734049f14293.html)\).
-   URL approach: By using a plain URL and setter methods to provide the needed configuration directly in the coding.

All of the listed approaches above require an existing consumption model.

> ### Note:  
> In on-premise systems, SOAP services are configured by logical ports, which are maintained in transaction `SOAMANAGER`. In the ABAP environment, the concept of logical ports has been replaced by the concept of SOAP destination objects.

**Related Information**  


[SOAP Communication via Communication Arrangements](soap-communication-via-communication-arrangements-2133e15.md "")

[SOAP Communication via Destination Service](soap-communication-via-destination-service-72bb6b5.md)

[SOAP Communication via URL](soap-communication-via-url-7e22ed9.md)

