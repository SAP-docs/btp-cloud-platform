<!-- loio64e99bb5291940489bd2277ee027d82e -->

# Audit Log Write API for Customers

The SAP Audit Log service provides an Audit Log Write API for customers, which enables the recording of audit relevant events.



<a name="loio64e99bb5291940489bd2277ee027d82e__section_flw_kmc_byb"/>

## Categories of Audit Relevant Events

There are four categories of audit relevant events:

1.  Log read access to sensitive personal data

    Use a data-accesses audit log record for the cases where an access to personal data is executed. The audit log contains information on the accessed personal data, as well as the full information of the user that is accessing the personal data, the owner of the personal data \(the Data Subject\), and the identifier of the place where the access to the personal data have been executed \(the Object\).

    Examples of personal data access events are all the read accesses sensitive personal data, which means information on racial or ethnic origin, political opinions, religious or philosophical beliefs, trade-union membership, health or sex life, bank account and credit card data, genetic data and bio-metric data for the purpose of uniquely identifying a natural person.

2.  Log changes to personal data

    Use a data-modification audit log record for the events that are related to modification of personal data. The audit log contains information on the modified personal data, as well as the full information of the user that is accessing the personal data, the owner of the personal data \(the Data Subject\)t, and the identifier of the place where the access to the personal data have been executed \(the Object\).

    Examples of personal data modification events are writing, deleting, or changes on an address, e-mail address, phone number, and any other data that can lead to a persona identification.

3.  Security event log

    Log security data for all events that might have an impact over the system security. Examples for such events are successful and non-successful login and logout events, changes in access control permissions, changes in credentials, changes in sensitive configurations, and so on.

4.  Configuration change log

    Use the configuration change audit log events for various changes in configurations. The audit log contains the changed configuration parts with old and new value. Log only the changed parts with the old and new value. If old or new value doesn't exist in case of adding a new property or deleting one respectively, skip the missing values or set them as null.

    Examples of configuration change events are creation/deletion of service instances, binding/unbinding service instances, software update, changes in configurations, and so on.




<a name="loio64e99bb5291940489bd2277ee027d82e__section_rcv_smc_byb"/>

## Prerequisites for using the Audit Log Write API for Customers



### Enablement and entitlements

As a first step to use the Audit Log Write API, make sure that the service is enabled for your subaccount and that there is an entitlement for the premium plan of the service.

If the “Audit Log Service” of plan “premium” is not visible from the account cockpit service marketplace for your subaccount, do the following to entitle the service:

-   To add entitlements on subaccount level, navigate to the subaccount via the account cockpit and choose *Entitlements* \> *Configurate Entitlements*

-   To add entitlements on global account level via the account cockpit, navigate to the account cockpit global account view and choose *Entitlements* \> *Service Assignments*
-   To add entitlements for a global account via the SAP BTP Control Center, choose the global account and go to *Edit* \> *assign services*. To select the Auditlog Service checkbox choose *Next* \> *Set Entitlements* \> *Select Auditlog Service* and ensure that there is quota for the “premium” plan of the service in the desired region\(s\).



### Creation of a service instance

The “premium” plan of the auditlog service uses mTLS authentication via X.509 certificates. To create a service instance via the account cockpit, do the following:

1.  Select the “premium” plan for the service instance creation from the Service Marketplace inside the SAP BTP Cockpit.
2.  Choose a runtime and a name for the service instance.
3.  Specify a unique “xsappname” per subaccount for each instance and provide the x509 authentication parameters during service instance creation.

    You can also create a service instance via the CF client with the following command:

    ```
    cf api <cf-domain>
    cf login
    cf target -o <desired-org> -s <desired-space>
    cf create-service auditlog premium <my-service-instance> -c '{
      "xs-security": {"xsappname": "<some-unique-name>",
            "oauth2-configuration": {
                "credential-types": ["x509"],
                "grant-types": ["client_x509","client_credentials"]
        }
      }
    }'
    
    ```




### Creation of a service key

The service keys provide credentials and URLs for interacting with your service instance. You can create a service key in one of the following ways: from the account cockpit or via CF command.

-   From your account cockpit, select the created “premium” service instance from the *Instances and Subscriptions* section. Depending on the chosen runtime environment, you can see a *Create* button for either a service key or a service binding. In the service key/binding creation box, specify the validity of the X.509 certificates used for authentication.
-   In the CF client, use the following command. The example parameters sets the certificate credentials validity to 30 days. After that period, the credentials expire and need to be rotated. For more information about the rotation, see the *Credentials rotation* section.

    ```
    cf create-service-key <my-service> <my-key> -c '{
      "xsuaa": {
      "credential-type": "x509",
      "x509": {
        "key-length": 2048,
        "validity": 30,
        "validity-type": "DAYS"
       }
      }
    }'
    
    ```




### Creation of a service binding

Like service keys, the classical service bindings provide credentials and endpoints for using a service instance and are mainly intended to be used with Cloud Foundry applications. You can bind a CF application to one or more service instances. As a result, in the VCAP\_SERVICES application environment variable there is a dedicated JSON object for each service binding.

You can perform the binding operation directly from the account cockpit settings of the application, via the CF client, or via the application deployment manifest. Specifically for the Audit Log Write API “premium” plan, it is important to provide the credentials parameter to enable the provisioning of X.509 certificates. Examples:

-   Create a service binding via the CF client:

    ```
    cf bind-service <sample-application> <auditlog-premium-service-instance> -c '{
      "xsuaa": {
      "credential-type": "x509",
        "x509": {
          "key-length": 2048,
          "validity": 30,
      "validity-type": "DAYS"
        }
      }
    }'
    
    ```

-   Create a service binding through a simple deployment manifest:

    ```
    ---
    applications:
    - name: java-auditlog-sample
      memory: 512M
      instances: 1
      path: target/java-auditlog-sample.war
      env:
        TARGET_RUNTIME: tomcat
      services:
        - name: "<auditlog-premium-service-instance-name>"
          parameters:
            xsuaa:
              credential-type: "x509"
              x509:
                key-length: 2048
                validity: 30
                validity-type: "DAYS"
    
    ```

-   Create a service binding through an MTA deployment manifest:

    ```
    modules:
    - name: <module using the Audit Log Service>
      requires:
        - name: <Audit Log Service Premium Instance Name>
          parameters:
            config:
              xsuaa:
                credential-type: x509
                x509:
                  key-length: 2048
                  validity: 2
                  validity-type: MONTHS
     - name: <other modules>
    
    resources:
    - name: <Audit Log Service Premium Instance Name>
        type: org.cloudfoundry.managed-service
        parameters:
          service: auditlog
          service-plan: premium
    
    ```




### Authentication and authorization

This section describes the approach to obtain credentials for authentication and authorization towards the Audit Log Write API.

-   Retrieving service-key information

    When you create a service key or binding, do one of the following:

    -   Download the service-key data from the account cockpit - select the three dots next to the service key/binding and then *Download*.

    -   Use the following CF command extract the data from the service key -`cf service-key <my-service> <my-key>`. Example of a sample service key or binding object:

        ```
        {
          "uaa": {
            "apiurl": "https://api.authentication.<cf_domain>",
            "certificate": "<x509_certificate>",
            "certificate-pinning": true,
            "certurl": "https://<subdomain>.authentication.cert.<cf_domain>",
            "clientid": "<client_id>",
            "clientx509enabled": true,
            "credential-type": "x509",
            "identityzone": "<identitiy_zone>",
            "identityzoneid": "<identitiy_zone_id>",
            "key": "<private_key>",
            "sburl": "https://internal-xsuaa.authentication.<cf_domain>",
            "subaccountid": "<subaccount_id>",
            "tenantid": "<tenant_id>",
            "tenantmode": "dedicated",
            "uaadomain": "authentication.<cf_domain>",
            "url": "https://<subdomain>.authentication.<cf_domain>",
            "verificationkey": "<verification_key>",
            "xsappname": "<xsappname>",
            "zoneid": "<zone_id>"
          },
          "url": "https://api.auditlog.<cf_domain>:6081",
          "vendor": "SAP"
        }
        
        ```


-   Obtaining credentials for using the Audit Log Write API

    The service key/binding information you retrieve in the previous step, contains the issued client certificates for authentication and the URLs to query the service. You need to use those certificate credentials to issue a JWT token for authentication towards the Write API.

    To prepare a request for issuing a JWT token, extract the PEM certificates and the relevant service data. Extract clientid, certurl, certificate and key from the credentials for the audit log service instance. Save the extracted certificate and key to files in ".pem" format by removing all "\\n" entries.

    You can use the following example, considering that the service key/binding information is saved to a json file and use the `cat` and `jq` commands can be used for parsing the file:

    ```
    cat customer-write-api-demo-sk.json | jq --raw-output .uaa.certurl
    
    cat customer-write-api-demo-sk.json | jq --raw-output .uaa.clientid
    
    cat customer-write-api-demo-sk.json | jq --raw-output .url
    
    cat customer-write-api-demo-sk.json | jq --raw-output .uaa.certificate > mtls-certificate.pem
    
    cat customer-write-api-demo-sk.json | jq --raw-output .uaa.key > mtls-private-key.pem
    
    ```

    Then execute a POST request to `<uaa.certurl>oauth/token` using the client certificates. Use the following parameters in the request:

    ```
    URL: <value of "uaa.certurl">/oauth/token?grant_type=client_credentials&client_id=<value of "uaa.clientid">
    Method: POST
    Authentication Method: Client Certificates
    Certificate: <Value of "uaa.certificate">
    Key: <Value of "uaa.key">
    grant_type: client_credentials
    client_id: <Value of "uaa.clientid">
    
    ```

    Example of such a request using “curl”:

    ```
    curl --cert <path to certificate.pem> --key <path to key.pem> --request POST https://<value of "uaa.certurl">/oauth/token -d 'grant_type=client_credentials&client_id=<Value of "uaa.clientid">'
    ```

    You can also execute the JWT token request via REST client, like Postman. In such case, make sure to configure the certifciates in the Postman settings as described at [https://learning.postman.com/docs/sending-requests/certificates/](https://learning.postman.com/docs/sending-requests/certificates/).

    Pass the issued JWT token in the Authorization header when calling the Audit Log Server Write REST API: `Authorization: Bearer <token-value>`. Example:

    ```
    curl --location --request POST 'https://api.auditlog.<url-host>:6081/audit-log/oauth2/v2/configuration-changes' \
    --header 'Content-Type: application/json' \
    --header 'Authorization: Bearer <token> \
    --data-raw ‘{message-content}’
    
    ```

    Fore more examples, see section *Example requests for the Audit Log Write API*.

    The JWT token has a limited validity. When the token validity expires, you can issue a new one with the same set of certificate credentials.




### Credentials rotation

Once the validity of the certificate credentials from the service key/binding expire, the credentials for using the Audit Log service become invalid until the certificates are rotated. Make sure that the credentials are properly rotated before expiry to avoid issues using the Audit Log service.

For the case of CF apps with service bindings, the credentials rotation can be achieved by recreating the service binding with the auditlog service instance \(cf unbind-service; cf bind-service\). On each bind operation a new set of x509 certificates is generated.

For the case of apps using auditlog credentials from an auditlog service key, the credentials can be rotated by creating a new service-key and extracting the certificates and private-key from the newly created key.

From security perspective is not recommended to use very long validity period for the mTLS credentials and it is encouraged that the certificates are being rotated as frequently as possible \(depending on the use-case and application lifecycle\).



<a name="loio64e99bb5291940489bd2277ee027d82e__section_srm_dnc_byb"/>

## Audit Log Write REST API specifics



### Endpoints

The endpoints exposed for the “premium” service plan for the 4 types of audit log categories are the following, where the <host\> can be obtained from the service key/binding:

-   https://api.auditlog.<host\>:6081/audit-log/oauth2/v2/security-events
-   https://api.auditlog.<host\>:6081/audit-log/oauth2/v2/configuration-changes
-   https://api.auditlog.<host\>:6081/audit-log/oauth2/v2/data-accesses
-   https://api.auditlog.<host\>:6081/audit-log/oauth2/v2/data-modifications



### Response status codes

The following response status codes can be returned from the Audit Log Write API:

-   201 \(Created\): audit log successfully created

-   400 \(Bad Request\):

    -   URI syntax error

    -   Invalid attributes

    -   Cannot parse the received audit log message

    -   Connection shutdown


-   401 \(Unauthorized\): Missing or invalid "Authorization" header

-   413 \(Payload Too Large\): The Audit log message size is too big

-   429 \(Too Many Requests\): Rate limit per tenant \(provider\_tenant,org,space\) is hit

-   500 \(Internal Server Error\): If an unexpected exception occurred

-   502 \(Bad Gateway\): Load balancer issue

-   503 \(Service Unavailable\): Global rate limit is hit

-   504 \(Gateway Timeout\): Load balancer issue




### Audit Log message format

The audit log record contains the following two main parts - the first one is filled in by the user of the audit log service and the second one, mainly in the metadata part of the message, is filled in by the audit logging framework.

**Filled by the audit log user**


<table>
<tr>
<th valign="top">

Field



</th>
<th valign="top">

Semantics



</th>
</tr>
<tr>
<td valign="top">

uuid



</td>
<td valign="top">

Unique identifier of the message.



</td>
</tr>
<tr>
<td valign="top">

time



</td>
<td valign="top">

The time when the auditable event has been executed.



</td>
</tr>
<tr>
<td valign="top">

user



</td>
<td valign="top">

The user that is logged in and performs the auditable action. To let the server-side extract the user from the JWT token, set the “$USER” string, or set a custom user and set a custom field.



</td>
</tr>
<tr>
<td valign="top">

data\_subject



</td>
<td valign="top">

The persona that is the owner of the personal data, which is being accessed or modified in Log read access to sensitive personal data events and Log changes to personal data.



</td>
</tr>
<tr>
<td valign="top">

object



</td>
<td valign="top">

The unique identificator for the location of the personal data that is being accessed or modified in case of Log read access to sensitive personal data events and Log changes to personal data, as well as the unique identificator of the location and configuration that is being changed.



</td>
</tr>
<tr>
<td valign="top">

attributes



</td>
<td valign="top">

The list of attributes that are either added, deleted, or modified. There are three scenarios, for example:

1.  a new address is added - only fill in the new value for the attribute with the newly written value \(skip the old value\);
2.  an existing address is modified – add the changed value as new and the previous value as old;
3.  an existing address is deleted - fill in only the deleted value as the old value for the attribute \(skip the new value field\).



</td>
</tr>
<tr>
<td valign="top">

attachment



</td>
<td valign="top">

The list of attachments that contain a personal data and has been opened for reading by a user, and which must be reflected in an audit log entry.



</td>
</tr>
<tr>
<td valign="top">

ip



</td>
<td valign="top">

The IP where the audited security-relevant event is executed \(only available for security audit log events\).



</td>
</tr>
<tr>
<td valign="top">

data



</td>
<td valign="top">

The message that contains the needed information for the logged security event \(only available for security audit log events\).



</td>
</tr>
<tr>
<td valign="top">

tenant



</td>
<td valign="top">

The identifier of the owner of the audit log message. Each audit log entry can have only single tenant equal to the zone ID, which determines the subaccount that is the owner of the message. The message is visible only for users in a role that has permissions to read the audit logs for this subaccount. The retention of the audit log message is determined based on the setup retention for this subaccount. For the premium plan, set the string “$PROVIDER”, which lets the servers extract the tenant zone ID automatically from the used JWT token.



</td>
</tr>
<tr>
<td valign="top">

success



</td>
<td valign="top">

The field is used for transactional messages only. When you mean to log the action as intention, skip the success field. If with the audit log message you mean to confirm the success of the action execution or to state that it was not successful, add the “success” field with values TRUE or FALSE.



</td>
</tr>
</table>

**Filled by the framework**


<table>
<tr>
<th valign="top">

Field



</th>
<th valign="top">

Semantics



</th>
</tr>
<tr>
<td valign="top">

service\_instance\_id



</td>
<td valign="top">

The GUID of the audit log instance that is used to write audit logs.



</td>
</tr>
<tr>
<td valign="top">

platform



</td>
<td valign="top">

The platform identifier together with the region information from where the audit log is written.



</td>
</tr>
<tr>
<td valign="top">

org\_name



</td>
<td valign="top">

Empty in the newest version for security reasons.



</td>
</tr>
<tr>
<td valign="top">

org\_guid



</td>
<td valign="top">

The organization GUID of the component that is using the audit log service to write audit logs.



</td>
</tr>
<tr>
<td valign="top">

space\_name



</td>
<td valign="top">

Empty in the newest version for security reasons.



</td>
</tr>
<tr>
<td valign="top">

space\_guid



</td>
<td valign="top">

The space GUID of the component that is using the audit log service to write audit logs.



</td>
</tr>
<tr>
<td valign="top">

app\_name



</td>
<td valign="top">

Empty in the newest version for security reasons.



</td>
</tr>
<tr>
<td valign="top">

app\_guid



</td>
<td valign="top">

The GUID of the application that is using the audit log service to write audit logs.



</td>
</tr>
<tr>
<td valign="top">

category



</td>
<td valign="top">

Message category is set implicitly by the framework.



</td>
</tr>
</table>



<a name="loio64e99bb5291940489bd2277ee027d82e__section_npk_4nc_byb"/>

## Example Requests for the Audit Log Write API

This section contain examples for writing audit log events using “curl” demo purposes. You can use any other client, the examples serve to demonstrate the structure of the required payload per each audit log type.



### Writing a security event

Mandatory fields: "uuid", "user", "tenant", "time", "data", "tenant".

```
curl --location --request POST 'https://api.auditlog.cf.<host>:6081/audit-log/oauth2/v2/security-events' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <JWT-token-value> \
--data-raw '{
  "uuid": "E2B74CFF-C7C2-4A78-BF6A-337E3431884E",
  "user": "$USER",
  "time": "2023-06-30T00:00:00.000Z",
  "ip": "127.0.0.1",
  "data": "Demo security event message.",
  "tenant": "$PROVIDER"
}'

```



### Writing a configuration change event

Mandatory fields: "object\_id", "uuid", "user", "tenant", "time", "attributes".

```
curl --location --request POST 'https://api.auditlog.cf.<host>:6081/audit-log/oauth2/v2/configuration-changes' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <JWT-token-value>\
--data-raw '{
  "uuid": "57DF4DFB-2352-4330-8E3C-027ABB02037C",
  "user": "test-als-user@sap.com",
  "time": "2023-06-30T00:00:00.000Z",
  "id": "1A5511ED-4730-49C9-A5FC-83BB63CA4B88",
  "tenant": "$PROVIDER",
  "object": {
    "type": "name of an attribute",
    "id": {
      "key1": "value1",
      "key2": "value2"
    }
  },
  "attributes": [
    {
      "name": "cfg attribute 1",
      "old": "old cfg attribute 1 value",
      "new": "new cfg attribute 1 value"
    },
    {
      "name": "cfg attribute 2",
      "old": "old cfg attribute 2 value",
      "new": "new cfg attribute 2 value"
    }
  ],
  "category": "audit.configuration",
  "customDetails": {
      "customKey": "customValue",
      "arbitraryKey": "arbitraryValue",
      "customJson": {
          "testString1": "testValue1",
          "testString2": "testValue2"
      }
  }
}'

```



### Writing a data modification event

Mandatory fields: "object\_id", "user", "tenant", "time", "attributes".

```
curl --location --request POST 'https://api.auditlog.cf.<host>:6081/audit-log/oauth2/v2/data-accesses' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <JWT-token-value>\
--data-raw '{
  "uuid": "48235F10-4F67-4621-8919-D0E2F7DBB81D",
  "user": "some-user-id",
  "identityProvider" : "$IDP",
  "time": "2023-06-30T00:00:00.000Z",
  "tenant" : "$PROVIDER",
  "object": {
      "type": "online system",
      "id": {
        "name" : "Students info system",
        "module" : "Admin module"
      }
  },
  "data_subject": {
      "type": "student",
      "role": "foreign student",
      "id": {
		"student_id":"12345678",
		"first name":"Jane",
		"last name":"Smith"
      }
  },
  "attributes": [
    {
      "name": "name of attribute 1"
    },
    {
      "name": "name of attribute 2",
      "successfull": true
    }
  ],
  "customDetails" : {
    "customKey" : "customValue",
    "anotherCustomKey" : "another custom value",
    "customJson": {
      "testString1": "testValue1",
      "testString2": "testValue2"
    }
  },
  "attachments": [
      {
          "id": "someId",
          "name": "attachmentName",
          "content": "attachmentContent"
      }
  ]
}'

```



### Writing a data access event

Mandatory fields: "object\_id", "user", "tenant", "time", "attributes".

```
curl --location --request POST 'https://api.auditlog.cf.<host>:6081/audit-log/oauth2/v2/data-modifications' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <JWT-token-value> \
--data-raw '{
  "uuid": "E5132C63-E5E6-4DF3-A59A-35861E1A145D",
  "user": "$USER",
  "time": "2023-06-30T00:00:00.000Z",
  "object": {
    "type": "DEMO Instance",
    "id": {
      "serviceInstanceId": "A2482034-B91D-4D0F-96BA-275C3255C983"
    }
  },
  "data_subject": {
    "type": "credentials",
    "role": "authentication",
    "id": {
      "key1": "value1",
      "key2": "value2"
    }
  },
  "attributes": [
    {
      "name": "old attribute",
      "new": "new attribute"
    }
  ],
  "id": "A0FD7483-A4B3-498D-83D7-2F5A518E53F2",
  "category": "audit.data-modification",
  "tenant": "$PROVIDER",
  "customDetails": {}
}'

```



<a name="loio64e99bb5291940489bd2277ee027d82e__section_itb_tnc_byb"/>

## Getting support

If you need support for Audit Log Write API, open a SNOW support ticket to the component “BC-CP-CF-SEC-AUDITLG”.

