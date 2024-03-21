<!-- loio8d578be04f034efdbd563635a0bfa8f8 -->

# Rate Limiting Rules

API requests to the SAP Usage Data Management service for SAP BTP are subject to rate limits.

Rate limits restrict the number of requests made by a caller within a defined time period. For authenticated requests, callers are identified by the authenticated user name, the tenant ID or the OAuth client ID. For non-authenticated requests, callers are identified by the originating IP address.

When you exceed the rate limit, you receive the HTTP response status code *429 Too Many Requests*.

The rate limits are:

-   The rate limit per authentication token or IP is 120 requests per second.

-   The maximum payload body size per request is 80 MB.


> ### Example:  
> For example, if you try to perform more than 120 GET requests to the `/reports/v1/monthlyUsage` endpoint in less than 1 second, you receive the following error:
> 
> ```
> <html>
> <head><title>429 Too Many Requests</title></head>
> <body>
> <center><h1>429 Too Many Requests</h1></center>
> <hr><center>openresty</center>
> </body>
> </html>
> 
> ```

