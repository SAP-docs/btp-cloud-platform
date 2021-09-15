<!-- loio24ee0ddd581247da80395f81448b0209 -->

# Performance Statistics

The application router provides performance statistics in an HTTP response header if the HTTP request contains an HTTP query parameter \(URL parameter\) `sap-statistics=true` or if the HTTP request contains an HTTP header field `sap-statistics:true`.

If an HTTP request that contains a header field or query parameter with `sap-statistics=true` reaches the application router, the application router forwards an `sap-statistics` header to the corresponding backend. If SAP statistics is implemented for the backend, the backend returns to the application router a response header containing the statistics information from the backend.

The application router returns the following statistics information in an `sap-statistics` response header:

-   `total`: The time that has passed between the moment when the request entered into the application router and the moment when the application router started writing the response

-   `ext` \(in case of destination forwarding\): The time spent in the backend


Each backend sub-component can add its own response header with duration measurements when it receives the HTTP header `sap-statistics:true`.

