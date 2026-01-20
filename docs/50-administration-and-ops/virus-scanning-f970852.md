<!-- loiof9708520290640018ece3527694a4a8f -->

# Virus Scanning

SAP BTP ABAP environment applies virus scans on uploaded external data via OData service calls for fields of type `binary` to detect malicious or suspicious content.

In case malicious code is reported for binary content, it will be rejected and can't be processed any further. We also highly recommend common client protection tools, such as virus scanners on the clients.

> ### Note:  
> Note that for the following scenarios automatic virus scanning is not available:
> 
> -   During the processing of requests of object type `HTTP Service`
> 
> -   During `Read` operations
> 
> -   For data types other than `binary` \(like `string`, for example\)

