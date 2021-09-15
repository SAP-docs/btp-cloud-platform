<!-- loio985a0fd9555d4aaf9c20605cc79b112b -->

# Asynchronous Processing for Service Provisioning

A *Prefer* header with a `respond-async` preference allows clients to process a data service request asynchronously.

When a client has specified `respond-async` in the *Prefer* header of a data service request, the request can be processed asynchronously. The service responds with *202 Accepted* and a *Location* header with the location `/sap/opu/odata4/async_monitor/StatusMonitorEntries/<GUID>` is returned. This location leads to a status monitor resource that displays the current state of the asynchronous processing. The `asyncresult` header shows the number of asynchronous processes.

In addition, an optional *Retry-After* header indicates the time in seconds the client should wait before querying the service for status.

> ### Note:  
> If you want to read the response in asynchronous requests, but the response is not available yet, the retry time interval to read the response exponentially increases after each failed attempt. The max interval time is 2048 seconds.

