<!-- loio77b217b3f57a45b987eb7fbc3305ce1e -->

# Rate Limiting

Describes how all API requests to the SAP Cloud Management service for SAP BTP adhere to rate limiting rules.

Every API endpoint defines its own custom rate limit rule for the number of requests per time window and per identified caller.

Authenticated requests are associated either with the authenticated username, tenant ID or with the OAuth client ID. Unauthenticated requests are associated with the originating IP address, and not the user making requests.

When the rate limit is exceeded, the client receives the HTTP *429* Too Many Requests response status code.



<a name="loio77b217b3f57a45b987eb7fbc3305ce1e__section_zbv_2cm_53b"/>

## Response Example

For example, if you try to perform more than five GET requests to the `/accounts/v1/globalAccounts` endpoint in the `accounts-service` in less than a three second time window, you will receive the following error:

```
HTTP/1.1 429 Too Many Requests
{
  "error": {
    "code": 11006,
    "message": "Request rate limit exceeded.",
    "target": "/accounts/v1/globalAccounts",
    "details": [
      {
        "code": 11007,
        "message": "Maximum request rate limit is <X> requests in <Y> seconds"
      }
    ]
  }
}

```

> ### Note:  
> -   The error code for the rate limit exceeded error is always *11006* and the details contains the list of exceeded rate limit rules with the *11007* error code.
> -   No HTTP headers are returned to show your current rate limit status \(for example, the number of requests remaining in the current rate limit window\).

