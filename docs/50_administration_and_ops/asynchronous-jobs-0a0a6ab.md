<!-- loio0a0a6ab0ad114d72a6611c1c6b21683e -->

# Asynchronous Jobs

Describes the asynchronous calls that are supported by some functionality from the SAP Cloud Management service for SAP BTP.

When the API responds with the status code *202*, the request can be processed as an asynchronous job.

The status of the request can be fetched using the path provided in the *Location* header. The response of the API provided in the *Location* header is normally:

```
{
  "status": "<IN_PROGRESS/COMPLETED/FAILED>",
  "description": "<meaningful description in case one needed>"
}
```

> ### Note:  
> The response includes the `status` \(always\) and `description` \(optional\) fields.

For example, you can trigger a brand new job.

