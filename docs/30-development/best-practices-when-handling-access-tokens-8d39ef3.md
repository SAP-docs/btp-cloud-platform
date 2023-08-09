<!-- loio8d39ef36427f489aa50c8e4e12c336d0 -->

# Best Practices When Handling Access Tokens

Calls to SAP Authorization and Trust Management service can fail for many reasons, including network latency, connection errors, service downtime, idle connections closed by routing components and so on. The following sections provide recommendations on when to retry connections and the caching of tokens.

How your application handles access tokens has an impact on its resiliency. Cache tokens to avoid running into the rate limiting restrictions of the SAP Authorization and Trust Management service. Retry with cached tokens instead of always getting a new one.



<a name="loio8d39ef36427f489aa50c8e4e12c336d0__section_izc_qzn_fyb"/>

## Retry Mechanism

When your application or service tries to get a token and fails, retry the connection. A retry mechanism helps your application handle temporary issues. We recommend retrying token retrieval three times by default. The following table lists when to retry and how often.

**Retry and Backoff for Different HTTP Responses**


<table>
<tr>
<th valign="top">

Event Type



</th>
<th valign="top">

HTTP Status Code



</th>
<th valign="top">

Retry



</th>
<th valign="top">

Backoff Policy



</th>
</tr>
<tr>
<td valign="top">

Connection error



</td>
<td valign="top">

None



</td>
<td valign="top">

Yes, retry up to three times.



</td>
<td valign="top" rowspan="2">

Initial retry after 300 ms with a multiplier of 2.



</td>
</tr>
<tr>
<td valign="top">

Timeout



</td>
<td valign="top">

-   408: Request timeout

-   502: Bad gateway

    For example, request timeout from a Cloud Foundry Gorouter.

-   504: Gateway timeout




</td>
<td valign="top">

Yes, retry up to three times.



</td>
</tr>
<tr>
<td valign="top">

Rate Limiting



</td>
<td valign="top">

429: Too many requests



</td>
<td valign="top">

Yes, retry up to three times.



</td>
<td valign="top">

Base retry on the `Retry-After` header.



</td>
</tr>
<tr>
<td valign="top">

Other Events



</td>
<td valign="top">

-   500: Internal server error

-   503: Service unavailable




</td>
<td valign="top">

Yes, retry up to three times.



</td>
<td valign="top">

Initial retry after 1000 ms with a multiplier of 3.



</td>
</tr>
<tr>
<td valign="top">

Access Control



</td>
<td valign="top">

-   401: Unauthorized

-   403: Forbidden




</td>
<td valign="top">

No, don't retry.



</td>
<td valign="top">

None.



</td>
</tr>
</table>



<a name="loio8d39ef36427f489aa50c8e4e12c336d0__section_fzh_ccp_fyb"/>

## Token Cache

We recommend that you cache access tokens in your application as long as they're valid, instead of always getting a new token. If you constantly get a new token, you risk running up against the rate limits in the service and downtime for your application.

For more information, see .[Rate Limiting](../60-security/rate-limiting-d203e2d.md)

Having a local cache also improves the performance of your applications.

Implement a method to remove invalid tokens from your cache. When your application calls with a token from your cache and receives the return codes in the following table, remove the token from your cache and request a new token.

**Triggers for Removing Tokens from Your Cache**


<table>
<tr>
<th valign="top">

HTTP Status Code



</th>
<th valign="top">

Potential Causes



</th>
<th valign="top">

Application Response



</th>
</tr>
<tr>
<td valign="top">

401: Unauthorized



</td>
<td valign="top">

-   The signing key of the token was rotated.

    For more information, see [Rotate Signing Keys of Access Tokens](../50-administration-and-ops/rotate-signing-keys-of-access-tokens-b279adf.md).

-   Token expired and your application hasn't removed it from your cache yet.




</td>
<td valign="top" rowspan="2">

Remove the token from the cache and request a new token.



</td>
</tr>
<tr>
<td valign="top">

403: Forbidden



</td>
<td valign="top">

Occurs if the token is valid but a scope is missing.

> ### Note:  
> Scopes of the client or user can have changed during the caching period.



</td>
</tr>
</table>

> ### Tip:  
> SAP Authorization and Trust Management service ensures that key remain valid for 2 hours after key rotations. Exception: When subaccount administrators force a key rotation, the key is immediately invalid. We recommend that you configure your cache with a 2-hour time-to-live \(TTL\). If you use a longer TTL, your application must be able to invalidate cache entries when the service responds with 401. Have your application only retry once on failure.

> ### Restriction:  
> When administrators force key rotation, applications that use cached tokens must accept a downtime until their caches have been cleared.

**Related Information**  


[https://github.com/SAP/cloud-security-services-integration-library/tree/main/token-client\#cache-configuration](https://github.com/SAP/cloud-security-services-integration-library/tree/main/token-client#cache-configuration "cloud-security-services-integration-library on Github")

