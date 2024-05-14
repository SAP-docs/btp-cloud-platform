<!-- loio7db3c9f8eba74d9f90c9d07a3c0d7762 -->

# Audit Log Retrieval API for Global Accounts in the Cloud Foundry Environment

> ### Note:  
> The following procedure is applicable only for Feature Set B Global Accounts. To retrieve audit logs for Feature Set A Global Accounts, contact SAP support and include in your request: Global Account ID, recipient email, timeframe, and reason for the request. For more information about feature sets, see [Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md)

On Central regions, Audit Log Retrieval API allows you to retrieve audit logs written on behalf of your SAP BTP Global Account.

Your central region is the eu10 Europe \(Frankfurt\) region, unless your global account is located in the China \(Shanghai\) and Government Cloud \(US\) regions. Then use the landscape domain of your central region.

Audit Log Retrieval API is protected by OAuth, and to consume it, you need your system to generate and use a valid OAuth.

> ### Note:  
> After the audit logs are generated and sent to the Audit Log service, the logs are not immediately accessible for retrieval.

Retrieving of audit logs via Audit Log Retrieval API is limited to the size of the audit logs written on behalf of the global account. The possible request rate is now limited to:

-   4 requests per second per auth-token/tenant on CF-EU11, CF-EU30, CF-US20, CF-US21, CF-JP10, CF-JP20, CF-BR10. There is also a burst queue that can temporarily allow up to 20 requests per second.

-   8 requests per second per auth-token/tenant on CF-EU10, CF-EU20, CF-US10, CF-US30. There is also a burst queue that can temporarily allow up to 40 requests per second.


The API returns a HTTP 429 response code when the limit is exceeded.



<a name="loio7db3c9f8eba74d9f90c9d07a3c0d7762__section_xyx_ym3_t5b"/>

## Prerequisites

You do the following procedure through Cloud Foundry Environment, which is part of a subaccount. To enable Audit Log Retrieval API for Global Account \(Feature Set B\), you must perform the following prerequisite steps as a global account administrator:

1.  You need to have one or more subaccounts in the Central region<sup>\(1\)</sup>. Create one if needed.

    > ### Note:  
    > ALL space developer users can access the service instance in the subaccount where it's entitled. To restrict access to your global account audit logs we recommend, you create a new subaccount in the Central regions<sup>\(1\)</sup> and add only users eligible to read global account audit logs to it.


2.  Follow the steps to entitle one or more of your subaccounts with the **Central plan** of service Auditlog Management:

    1.  Navigate to your global account.

    2.  Choose *Entitlements* \> *Entity Assignments* from the left-hand side menu.
    3.  In the pop-up window, select all the subaccounts for which you would like to configure or display entitlements.
    4.  Choose *Select* to apply the filter.

        You get a table for each of the subaccounts you selected, which displays the current entitlement and quota assignments.

    5.  Choose *Configure Entitlements* to start editing entitlements for a particular subaccount. You can now edit the entitlements table.

        > ### Note:  
        > You can edit entitlements for only one subaccount at a time.

    6.  Choose *Add Service Plans*.
    7.  Select *Auditlog Management* from the list on the left-hand side.
    8.  Choose the checkbox of *Central plan* on the right-hand side.
    9.  Choose *Add 1 Service Plan*.
    10. Choose *Save* and exit edit mode for that subaccount.

3.  To execute the procedure, you need to have the `Space Developer` role for the corresponding Space.


> ### Note:  
> For security reasons, we strongly recommend you to re-create the `auditlog-management` Service-Instance bindings and service keys at least every 90 days.



<a name="loio7db3c9f8eba74d9f90c9d07a3c0d7762__section_pqn_1n3_t5b"/>

## Create Instance of the `auditlog-management` Service

1.  Create a Cloud Foundry Org and Space, in case you don't have any. See [Create Spaces](create-spaces-2f6ed22.md).

2.  Log in the Cloud Foundry landscape using the corresponding Cloud Foundry API \(Infrastructure/Landscape Overview\).

    ```
    cf login -a <API_URL> -o <ORG> -s <SPACE> -u <USER>
    ```

3.  Create a service instance of the service `auditlog-management`:

    > ### Note:  
    > For security reasons, we strongly recommend you to adopt the provided mutual TLS authentication \(mTLS\). The mTLS authentication relies on X.509 certificates for the verification of the parties in the network connection. Create the `auditlog-managenment` service instances with the additional parameters, as explained in the following mTLS points.

    -   \(Recommended\) For mTLS authentication using X.509 certificates, use:

        ```
        cf create-service auditlog-management central <SERVICE_INSTANCE> -c '{
            "xs-security": {
                "xsappname": "auditlog",
                "oauth2-configuration": {
                    "credential-types": [
                        "x509"
                    ],
                    "grant-types": [
                        "client_credentials"
                    ]
                }
            }
        }'
        ```

        > ### Note:  
        > The `xsappname` attribute from the service parameters JSON needs to have unique instance for each service. The `xsappname` attribute can hold an arbitrary string as value, which is not required to be `auditlog`. The code block serves only as example.

    -   For non-mTLS authentication, use


    `cf create-service auditlog-management central <SERVICE_INSTANCE>`

    > ### Note:  
    > If there's a previously created auditlog-management service instance without the security parameters for mTLS, we recommend you to delete that instance and create a new instance with mTLS authentication using the parameters from the previous \(recommended\) scenario.

4.  Create a key for the service instance:

    -   For service instances with mTLS, use:

        ```
        cf create-service-key <SERVICE_INSTANCE> <SERVICE_KEY> -c '{
            "xsuaa": {
                "credential-type": "x509",
                "x509": {
                    "key-length": 2048,
                    "validity": 1,
                    "validity-type": "DAYS"
                }
            }
        }'
        ```

        > ### Note:  
        > You can specify the validity period of the service key for each use case. To use the service instance, once the key validity expires, create a new key. By default and for security reasons, the key from this code example is created with a validity of 1 day.

    -   For service instances without mTLS, use:

    `cf create-service-key <SERVICE_INSTANCE> <SERVICE_KEY>`

5.  List the key of the service instance:

    `cf service-key <SERVICE_INSTANCE> <SERVICE_KEY>`

6.  Extract data from the service key.

    -   For mTLS scenario:

        -   Extract the values for `uaa.clientid` and `uaa.certurl` of the key of the service instance for access token creation.
        -   Extract the value for `url` and use it for later request to retrieve audit logs.
        -   Extract the value for `uaa.certificate`, remove all `\n` entries from the X.509 certificate, and save it as a file in the `.pem` format.
        -   Extract the value for `uaa.key`, remove all `\n` entries from the RSA private key, and save it as a file in the `.pem` format.

        > ### Note:  
        > To extract of the values and avoid errors while copying or removing characters, you can use the `sed` and `jq` tools:
        > 
        > ```
        > cf service-key <SERVICE_INSTANCE> <SERVICE_KEY> | sed '/Getting key/d' | jq --raw-output .uaa.certurl
        > cf service-key <SERVICE_INSTANCE> <SERVICE_KEY> | sed '/Getting key/d' | jq --raw-output .uaa.clientid
        > cf service-key <SERVICE_INSTANCE> <SERVICE_KEY> | sed '/Getting key/d' | jq --raw-output .url
        > # the following two commands save the output to .pem files on the location, where the command is executed
        > cf service-key <SERVICE_INSTANCE> <SERVICE_KEY> | sed '/Getting key/d' | jq --raw-output .uaa.certificate > mtls-certificate.pem
        > cf service-key <SERVICE_INSTANCE> <SERVICE_KEY> | sed '/Getting key/d' | jq --raw-output .uaa.key > mtls-private-key.pem
        > ```

    -   For non-mTLS scenario:

    Extract values for `uaa.url`, `uaa.clientid` and `uaa.clientsecret` of the key of the service instance for access token creation. Extract the `url` to be used for later request to retrieve audit logs.




<a name="loio7db3c9f8eba74d9f90c9d07a3c0d7762__section_sm3_gn3_t5b"/>

## Create an OAuth Access Token

1.  Request an OAuth access token

    -   For mTLS scenario

        To request the OAuth access token via the mTLS extracted X.509 certificates and RSA private key flow, execute an HTTP POST request with the following parameters:

        ```
        URL: <value of "uaa.certurl">/oauth/token?grant_type=client_credentials&client_id=<value of "uaa.clientid">
        Method: POST
        Authentication Method: Client Certificates
        Certificate: <Value of "uaa.certificate">
        Key: <Value of "uaa.key">
        grant_type: client_credentials
        client_id: <Value of "uaa.clientid">
        ```

        Example:

        ```
        curl --cert <path to certificate.pem> --key <path to key.pem> --request POST https://<value of "uaa.certurl">/oauth/token -d 'grant_type=client_credentials&client_id=<Value of "uaa.clientid">'
        ```

    -   For non-mTLS scenario

    Request the OAuth access token via the OAuth client credentials flow, by executing an HTTP POST request with the following parameters:

    ```
    URL: <value of "uaa.url">/oauth/token?grant_type=client_credentials
    Method: POST
    Authentication Method: Basic Authentication
    Username: <Value of "uaa.clientid">
    Password: <Value of "uaa.clientsecret">
    
    ```

2.  Extract the value of the `access_token` attribute from the JSON response.

    This token grants access to the audit logs of the subaccount on the landscape where the service instance is created.

    > ### Note:  
    > The token is valid for 12 hours.

    > ### Note:  
    > The content of the access token can be displayed using a standard JWT decoder




<a name="loio7db3c9f8eba74d9f90c9d07a3c0d7762__section_apw_mn3_t5b"/>

## Audit Log Retrieval

The Audit Log Retrieval API incorporates server-side paging to address the efficient handling of queries producing substantial result sets.

> ### Note:  
> The logs are not immediately accessible for retrieval

In instances where the query produces a result with significant size, the API systematically partitions the output into manageable chunks. The response includes an HTTP header featuring a handle, designed to facilitate the retrieval of subsequent result segments. To obtain additional portions of the result, pass the handle as a URL parameter in the subsequent retrieval request. The size of each chunk is predetermined, with a page size fixed at 500.

Supported request parameters:

-   `time_from and time_to`– if no time filter is specified the default timeframe of 30 days back is returned. Use the following format: 2018-05-11T10:42:00. The time is in UTC.

-   `handle` – in case the result set is too large, it's chunked, and a handle is returned for reading the next chunk. The handle is returned as a Response Header in the form: Paging: `handle=<value>`. Then you can provide `handle=<value>` as a request parameter in the subsequent retrieval request.

    > ### Note:  
    > The `handle` parameter is a base 64 encoded string. Don't attempt to decode it. Send the `handle` in the subsequent request exactly as received in the previous one, without any modification.




### Example: Get audit logs for the last 30 days

Execute the following HTTP GET request:

`<url_from_service_key>/auditlog/v2/auditlogrecords`

Provide the OAuth access token as an `"Authorization"` header: `"Authorization: Bearer <access_token>"` 

The response is in JSON format, containing the audit log entries, split on pages if needed.



### Example: Get audit logs filtering by time

Execute the following HTTP GET request:

`<url_from_service_key>/auditlog/v2/auditlogrecords?time_from=2018-05-10T10:42:00&time_to=2018-05-11T10:46:00`



### Example: Get audit logs next chunk determined by the server-side paging

Execute the following HTTP GET request:

`<url_from_service_key>/auditlog/v2/auditlogrecords?time_from=2018-05-10T10:42:00&time_to=2018-05-11T10:46:00&handle= <handle value>`

Response codes:

`HTTP Codes`

`HTTP 200 OK`

`HTTP 204 NO_CONTENT`

`HTTP 401 UNAUTHORIZED`

`HTTP 400 BAD_REQUEST`

`HTTP 403 FORBIDDEN`

`HTTP 429 Too Many Requests`

Predefined audit log message categories:

`'audit.security-events'`

`'audit.configuration'`

`'audit.data-access'`

`'audit.data-modification'`



<a name="loio7db3c9f8eba74d9f90c9d07a3c0d7762__section_ezs_wn3_t5b"/>

## Results

```
{
    "message_uuid": "e3a533c1-57b3-42b5-b514-8934ec5b6a6a",
    "time": "2018-10-04T08:12:00.239Z",
    "tenant": "c6da83a8-dc72-4374-b8f7-42b37a99XXXX",
    "org_id": "82f1da92-e5b3-4cc5-8c90-964165afXXXX",
    "space_id": "82f1da92-e5b3-4cc5-8c90-964165aXXXX",
    "app_or_service_id": "5fb40c3a-d36a-42c7-adc8-e4abd83dXXXX",
    "als_service_id": "c18f9b6d-a8af-431c-a187-749ebc59XXXX",
    "user": "test",
    "category": "audit.security-events",
    "format_version": "",
    "message": {
        "uuid": " e3a533c1-57b3-42b5-b514-8934ec5b6a6a ",
        "user": "test",
        "time": "2018-10-04T08:12:00.239Z",
        "ip": "10.58.183.15",
        "data": "{\"level\":\"INFO\",\"origin\":null,\"msgNo\":1,\"msgId\":\"a2cf08ee-eedd-455b-bbd6-    400d6b611116\",\"message\":\"ClientAuthenticationSuccess ('Client authentication success'): principal=sb-40ae21f3-5034-40dd-ac0d-0c9d3e0ebb06!b3034|auditlog-management!b3034, origin=[remoteAddress=52.58.183.15, clientId=sb-40ae21f3-5034-40dd-ac0d-0c9d3e0ebb06!b3034|auditlog-management!b3034], identityZoneId=[c6da83a8-dc72-4374-b8f7-42b37a99db2b]\",\"user\":null,\"version\":\"1.0\"}",
        "id": "cb046a0f-cc23-406b-a1d2-22ee6cf89a4d",
        "category": "audit.security-events",
        "tenant": "c6da83a8-dc72-4374-b8f7-42b37a99XXXX"
      }
}

```

