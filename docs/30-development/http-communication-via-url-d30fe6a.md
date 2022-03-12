<!-- loiod30fe6a295c74d8cb2fa2e641fbde495 -->

# HTTP Communication via URL

You can configure the URL static in the code:

> ### Sample Code:  
> ```abap
> DATA(lo_url_destination) = cl_http_destination_provider=>create_by_url(
>                                                 'https://<host>/sap/bc/srt/xip/sap/<provider>/000/<service>/<binding>').
> 
> ```

> ### Note:  
> Using `create_by_url` is only suitable for public services or test purposes, because credentials should be stored in the destination service, or using communication arrangements \(`create_by_comm_arrangement`, `create_by_cloud_destination`\).

**Related Information**  


[Set Up HTTP Communication](set-up-http-communication-3884bc3.md "The HTTP client allows to connect to HTTP endpoints.")

