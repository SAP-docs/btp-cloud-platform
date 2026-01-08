<!-- loio1d7207244caa464a81653ade7dd96cff -->

# SAP Java Buildpack: Properties

On this page you can find all the available properties, parameters, and environment variables to use in SAP Java Buildpack. You can filter by name, value, a word, or even part of a word.



## Properties & Parameters

****


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Description

</th>
<th valign="top">

Values

</th>
<th valign="top">

Example

</th>
</tr>
<tr>
<td valign="top">

`connector.maxHttpHeaderSize` 

</td>
<td valign="top">

The maximum size of the request and response HTTP header, specified in bytes

</td>
<td valign="top">

Default value: **8192** 

</td>
<td valign="top">

To configure the maximum size of the HTTP header, use:

```
env:
									JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomee/conf/server.xml': {'connector.maxHttpHeaderSize':1024}]"
```



</td>
</tr>
<tr>
<td valign="top">

`connector.maxPartHeaderSize` 

</td>
<td valign="top">

The maximum number of header bytes permitted per part in a request where the content type is `multipart/form-data` 

</td>
<td valign="top">

Default value: **512** 

</td>
<td valign="top">

To configure the maximum size of a header part, use:

```
env:
									JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomee/conf/server.xml': {'connector.maxPartHeaderSize':256}]"
```



</td>
</tr>
<tr>
<td valign="top">

`connector.maxPartCount` 

</td>
<td valign="top">

The maximum total number of parts permitted in a request where the content type is `multipart/form-data` 

</td>
<td valign="top">

Default value: **50** 

</td>
<td valign="top">

To configure the maximum number of parts in a request, use:

```
env:
									JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomcee/conf/server.xml': {'connector.maxPartCount':40}]"
```



</td>
</tr>
<tr>
<td valign="top">

`connector.maxPostSize`

</td>
<td valign="top">

The maximum size \(in bytes\) of the POST request, which will be handled by the container FORM URL parameter parsing. The limit can be disabled by setting the attribute's value to any integer number less than zero \(0\).

**Note:** You can use the [Failed Request Filter](https://tomcat.apache.org/tomcat-10.1-doc/config/filter.html#Failed_Request_Filter) to reject requests that exceed the default limit.

</td>
<td valign="top">

Default value:

**2097152** \(2 MiB\)

</td>
<td valign="top">

To configure the maximum size of the POST request, use:

```
env:
									JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomee/conf/server.xml': {'connector.maxPostSize':800000}]"
```



</td>
</tr>
<tr>
<td valign="top">

`connector.maxThreads` 

</td>
<td valign="top">

The maximum number of request-processing threads to be created by this Connector. It therefore determines the maximum number of simultaneous requests that can be handled.

</td>
<td valign="top">

Default value: **200** 

</td>
<td valign="top">

To configure the maximum number of request-processing threads, use:

```
env:
									JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomee/conf/server.xml': {'connector.maxThreads':800}]"
```



</td>
</tr>
<tr>
<td valign="top">

`connector.encodedSolidusHandling` 

</td>
<td valign="top">

A string value that configures request paths containing a `%2f` sequence.

</td>
<td valign="top">

Default value: **reject**

-   When set to **reject**, these request paths will be rejected with a 400 response.

-   When set to **decode**, these request paths will have that sequence decoded to **/** at the same time other `%nn` sequences are decoded.

-   When set to **passthrough**, these request paths will be processed with the `%2f` sequence unchanged.




</td>
<td valign="top">

To decode the `%2f` sequence of the request paths to **/**, use:

```
env:
									JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomee/conf/server.xml': {'connector.encodedSolidusHandling':'decode'}]"
```



</td>
</tr>
<tr>
<td valign="top">

`connector.allowTrace` 

</td>
<td valign="top">

A Boolean value that enables or disables the TRACE HTTP method

</td>
<td valign="top">

Default value: **false** 

</td>
<td valign="top">

To enable the TRACE HTTP method, use:

```
env:
									JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomee/conf/server.xml': {'connector.allowTrace':true}]"
```



</td>
</tr>
</table>



## Environment Variables

****


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Description

</th>
<th valign="top">

Values

</th>
<th valign="top">

Example

</th>
</tr>
<tr>
<td valign="top">

VCAP\_SERVICES

</td>
<td valign="top">

When you bind a service instance to your app and then restart the app, Cloud Foundry adds connection details to the VCAP\_SERVICES environment variable.

See: [VCAP\_SERVICES](https://docs.cloudfoundry.org/devguide/deploy-apps/environment-variable.html#VCAP-SERVICES)

</td>
<td valign="top">

See column **Example** 

</td>
<td valign="top">

```

$ cf env my-app

Getting env variables for app my-app in org my-org / space my-space as
admin...
OK

System-Provided:

{
 "VCAP_APPLICATION": {
  "application_id": "abcd-1234-0000-aaaa789-eeeeeeeeee",
  "application_name": "my-app",
  "application_uris": [
    "my-app.example.com"
  ],
  "application_version": "xyzxyz-3333-1234567890-aaaaaaaaaa",
  "cf_api": "https://api.example.com",
  "limits": {
    "disk": 1024,
    "memory": 256
  },
  "name": "my-app",
  "organization_id": "...",
  "organization_name": "my-org",
  "space_id": "...",
  "space_name": "my-space",
  "uris": [
    "my-app.example.com"
  ]
 }
}
```



</td>
</tr>
<tr>
<td valign="top">

VCAP\_SERVICES\_FILE\_PATH

</td>
<td valign="top">

It sets the path to the file containing the service binding information in JSON format. It must be enabled by an application feature flag.

See: [VCAP\_SERVICES\_FILE\_PATH \(experimental\)](https://docs.cloudfoundry.org/devguide/deploy-apps/environment-variable.html#VCAP-SERVICES-FILE-PATH)

</td>
<td valign="top">

See column **Example** 

</td>
<td valign="top">

-   Set the variable:

    ```
    
    VCAP_SERVICES_FILE_PATH=/etc/cf-service-bindings/vcap_services
    ```

-   To view the binding data, run:

    ```
    cf ssh <app_name> -c 'cat $VCAP_SERVICES_FILE_PATH'
    ```




</td>
</tr>
<tr>
<td valign="top">

JBP\_CONFIG\_RESOURCE\_CONFIGURATION

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

```

env:
  JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomcat/conf/server.xml': {'connector.maxHttpHeaderSize':1024}]"
```



</td>
</tr>
<tr>
<td valign="top">

JBP\_CONFIG\_COMPONENTS

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

```

env:
  JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
```



</td>
</tr>
<tr>
<td valign="top">

JBP\_CONFIG\_SAP\_MACHINE\_JRE

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

```

env:
  JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
  JBP_CONFIG_SAP_MACHINE_JRE: "[version: 11.+, memory_calculator_v2: {stack_threads: 266, class_count: 1001, headroom: 5}]"
```



</td>
</tr>
<tr>
<td valign="top">

JBP\_CONFIG\_SAP\_MACHINE\_JDK

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

```

env:
  JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
  JBP_CONFIG_SAP_MACHINE_JDK: "[ version: 11.0.22, memory_calculator_v2: {stack_threads: 266, class_count: 1001, headroom: 5}]"
```



</td>
</tr>
<tr>
<td valign="top">

JBP\_CONFIG\_JAVA\_OPTS

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

```

env:
  JBP_CONFIG_JAVA_OPTS: "[java_opts: '-Xms144M -Xss3M -Xmx444444K -XX:MetaspaceSize=66666K -XX:MaxMetaspaceSize=88888K']"
```



</td>
</tr>
<tr>
<td valign="top">

JBP\_CONFIG\_SAPJVM

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

```

env:
  JBP_CONFIG_SAPJVM: "[memory_calculator_v2: {stack_threads: 266, class_count: 1001, headroom: 5}]"
```



</td>
</tr>
<tr>
<td valign="top">

SET\_LOGGING\_LEVEL

</td>
<td valign="top">

It sets the log level of a logging location. You can do this before or during application deploy. You can set this variable in three ways:

-   In the **`manifest.yml`** file.
-   In a **`logback.xml`** file in directory `src/main/resources`.
-   In an **`application.properties`** file in directory `/src/main/resources/`.

See: [Logging and Tracing](logging-and-tracing-7eb922a.md)

</td>
<td valign="top">

Default log level: **INFO** 

</td>
<td valign="top">

```

env:
  SET_LOGGING_LEVEL: '{com.sap.sample.java.LogInfo: INFO, com.sap.sample.java.LogWarn: WARN}'
```



</td>
</tr>
</table>

