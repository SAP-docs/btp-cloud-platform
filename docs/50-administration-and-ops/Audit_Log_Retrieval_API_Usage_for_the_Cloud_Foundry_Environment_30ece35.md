<!-- loio30ece35bac024ca69de8b16bff79c413 -->

# Audit Log Retrieval API Usage for the Cloud Foundry Environment

The audit log retrieval API allows you to retrieve the audit logs for your SAP BTP Cloud Foundry environment account. It provides the audit log results as a collection of JSON entities.

The audit log retrieval API is protected by OAuth, and to consume it a valid OAuth client needs to be generated and used by the client system.

Retrieving of audit logs via the Audit Log Retrieval API is limited to the size of the audit logs generated for the account.



<a name="loio30ece35bac024ca69de8b16bff79c413__section_g1p_5gz_pfb"/>

## Prerequisites

The user executing the procedure is expected to have the `Space Developer` role for the corresponding Space.

> ### Note:  
> For security reasons it is strongly recommended the `auditlog-management` Service-Instances are recreated at least every 90 days.



<a name="loio30ece35bac024ca69de8b16bff79c413__section_yfz_xrt_pfb"/>

## Create instance of the `auditlog-management` service

1.  Create a Cloud Foundry Org and Space, in case you do not have any. See [Create Spaces](Create_Spaces_2f6ed22.md).

2.  Login to the Cloud Foundry landscape using the corresponding Cloud Foundry API \(Infrastructure/Landscape Overview\).

    ```
    cf login -a <API_URL> -o <ORG> -s <SPACE> -u <USER>
    ```

3.  Create a service instance of the service `auditlog-management`

    > ### Note:  
    > For security reasons, we strongly recommend you to adopt the provided mutual TLS authentication \(mTLS\). The mTLS authentication relies on X.509 certificates for the verification of the parties in the network connection, by creating the `auditlog-managenment` service instances with the additional parameters, as explained in the following mTLS points.

    -   \(Recommended\) For mTLS authentication using X.509 certificates, use:

        ```
        cf create-service auditlog-management default <SERVICE_INSTANCE> -c '{
        "xs-security": {"xsappname": "auditlog",
        "oauth2-configuration": {
        "credential-types": ["x509"],
        "grant-types": ["client_x509","client_credentials"]
        }
        }
        }
        ```

    -   For non-mTLS authetnication, use


    `cf create-service auditlog-management default <SERVICE_INSTANCE>`

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
        }
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
        -   Extract the value for `uaa.certificate`, remove all `\n` entries from the X.509 certificate and save it as a file in the `.pem` format.
        -   Extract the value for `uaa.key`, remove all `\n` entries from the RSA private key and save it as a file in the `.pem` format.

        > ### Note:  
        > To extract of the values and avoid errors while copying or removing characters, you can use the sed and jq tools:
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




<a name="loio30ece35bac024ca69de8b16bff79c413__section_l3t_p5t_pfb"/>

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
    **URL:** <value of "uaa.url">/oauth/token?grant_type=client_credentials
    **Method:** POST
    **Authentication Method:** Basic Authentication
    **Username:** <Value of "uaa.clientid">
    **Password:** <Value of "uaa.clientsecret">
    
    ```

2.  Extract the value of the `access_token` attribute from the JSON response.

    This token grants access to the audit logs of the subaccount on the landscape where the service instance is created.

    > ### Note:  
    > The token is valid for 12 hours.

    > ### Note:  
    > The content of the access token can be displayed using a standard JWT decoder




<a name="loio30ece35bac024ca69de8b16bff79c413__section_wgj_fvt_pfb"/>

## Audit Log Retrieval

The Audit Log Retrieval API supports server-side paging. If a given query produces a result with significant size, the result will be chunked. Then the response will contain an HTTP header with a handle, with which to retrieve the next chunks of the result. The handle can be passed via URL parameter in the subsequent retrieval request.

Supported request parameters:

-   `time_from and time_to`– if no time filter is specified the default timeframe of 30 days back is returned. The time should be provided in the following format: 2018-05-11T10:42:00. Times are UTC.

-   `handle` – in case the result set is too big, it will be chunked, and a handle will be returned for reading the next chunk. It is returned as a Response Header in the form: Paging: `handle=<value>`. Then `handle=<value>` can be provided as a request parameter in the subsequent retrieval request.




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

`<url_from_service_key>/auditlog/v2/auditlogrecords?handle=2018-06-14T10:11:18.968<4f932695-8616-4e1f-ac9a-1cdfb758f01d<2018-06-14T10:11:00.000`

`<url_from_service_key>/auditlog/v2/auditlogrecords?handle=<handle value>`

Response codes:

`HTTP Codes`

`HTTP 200 OK`

`HTTP 204 NO_CONTENT`

`HTTP 401 UNAUTHORIZED`

`HTTP 400 BAD_REQUEST`

`HTTP 403 FORBIDDEN`

Predefined audit log message categories:

`'audit.security-events'`

`'audit.configuration'`

`'audit.data-access'`

`'audit.data-modification'`



<a name="loio30ece35bac024ca69de8b16bff79c413__section_qyg_n5t_pfb"/>

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

**Related Information**  


[Audit Log Retrieval API for the Cloud Foundry Environment](https://api.sap.com/api/CFAuditLogRetrievalAPI/resource)

[API Documentation](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/4570e92cd29e419dbeee4caa1ef90701.html "API documentation for the Neo environment.") :arrow_upper_right:

