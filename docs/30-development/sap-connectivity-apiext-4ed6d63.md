<!-- loio4ed6d63105bd45578f73d7cf8c05d05c -->

# SAP Connectivity ApiExt

Use the SAP Connectivity ApiExt feature \(provided by SAP Java Buildpack\) to retrieve destination configurations or authentication headers ready to be used against the remote target system.

> ### Restriction:  
> SAP Connectivity ApiExt is only available for Tomcat application containers included in SAP Java Buildpack.
> 
> Also, Spring Boot works with SAP Connectivity ApiExt only when using WAR deployment.

> ### Note:  
> SAP Connectivity ApiExt is **not** the recommended way for consuming the Destination service as it only covers a subset of the service's APIs. It's primarily meant to be used internally by [SAP Java Connector](https://support.sap.com/en/product/connectors/jco.html) \(SAP JCo\) and for Neo migration scenarios, where there are limited possibilities to modify the code.
> 
> The **recommended** consumption mechanism for Java applications is [SAP Cloud SDK for Java](https://sap.github.io/cloud-sdk/docs/java/features/connectivity/btp-destination-service) or using the [Destination service REST API](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/destination-service-rest-api-23ccafbea18f4b65919a2799f2cd20e6-81).



<a name="loio4ed6d63105bd45578f73d7cf8c05d05c__section_vtc_w3g_hcc"/>

## Prerequisites

To use SAP Connectivity ApiExt during runtime, you first need to create:

-   A service instance for the Destination service
-   A destination entity in the Destination service that you want to retrieve from the application. See: [Managing Destinations](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/managing-destinations)
-   \(Optional\) A service instance for the Connectivity service – only needed if you plan to use it for destinations of type `ProxyType`=**OnPremise**



<a name="loio4ed6d63105bd45578f73d7cf8c05d05c__section_g2m_hhg_hcc"/>

## Activate the API

1.  Open the `pom.xml` file of your Tomcat-based Java application and add the following dependency:

    ```
    
    <dependency>
        <groupId>com.sap.cloud.connectivity.apiext</groupId>
        <artifactId>com.sap.cloud.connectivity.apiext</artifactId>
        <version>${connectivity-apiext.version}</version>
        <scope>provided</scope>
    </dependency>
    ```

2.  Now open the `manifest.yml` file and set environment variable USE\_CONNECTIVITY\_APIEXT to **true**:

    ```
    
    ---
    applications:
    - name: <APP_NAME>
      ...
      env:
        TARGET_RUNTIME: tomcat
        USE_CONNECTIVITY_APIEXT: true
    ```

3.  Bind the previously created service instances to your application. To do that, add their names at the end of the `manifest.yml` file. For example:

    ```
    
    ---
    applications:
    - name: <APP_NAME>
      ...
      env:
        TARGET_RUNTIME: tomcat
        USE_CONNECTIVITY_APIEXT: true
      services:
        - my_destination
        - my_connectivity
          ...
    ```


For more information, see [ConnectivityConfiguration API: Procedure](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/connectivityconfiguration-api?version=Cloud#procedure) 

**Related Information**  


[Create Destinations from Scratch](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/create-destinations-from-scratch)

[SAP Java Connector](sap-java-connector-3cee866.md "You can use the SAP Java Connector through the SAP Java buildpacks.")

