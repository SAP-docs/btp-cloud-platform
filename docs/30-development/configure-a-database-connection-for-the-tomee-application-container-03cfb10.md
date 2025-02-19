<!-- loio03cfb10c5b2042bd9cc0a1bc6bc6ba92 -->

# Configure a Database Connection for the TomEE Application Container



<a name="loio03cfb10c5b2042bd9cc0a1bc6bc6ba92__context_q5h_yxx_j2c"/>

## Context

> ### Note:  
> The examples below refer to TomEE 10 and SAP Java Buildpack 2.



<a name="loio03cfb10c5b2042bd9cc0a1bc6bc6ba92__steps_nqh_bx5_2fb"/>

## Procedure

1.  Create a **`resources.xml`** file.

    -   If the data source is to be used from a Web application, you have to create the file inside the **`WEB-INF/`** directory.

    -   If the data source is to be used from Enterprise JavaBeans \(EJBs\), you have to create the file inside the **`META-INF/`** directory.


    The **`resources.xml`** file has to be inside the application's WAR file, and has to contain information about the data source to be used.

    > ### Sample Code:  
    > *resources.xml*
    > 
    > ```
    > <?xml version='1.0' encoding='utf-8'?>
    > 
    > <resources>
    >  <Resource id="jdbc/DefaultDB" provider="xs.openejb:XS Default JDBC Database" type="javax.sql.DataSource" >
    >     service=${service_name_for_DefaultDB}
    >   </Resource>
    > </resources>
    > ```

2.  Add the default keys and their values. You need to include the data source information in directory **`META-INF/sap_java_buildpack_jakarta/config/resource_configuration.yml`** of the WAR file.

    -   Define a default service name for a Web application:

        > ### Sample Code:  
        > *resource\_configuration.yml*
        > 
        > ```
        > ---
        > tomee/webapps/ROOT/WEB-INF/resources.xml:
        >   service_name_for_DefaultDB: di-core-hdi
        > ```

    -   Define a default service name for an EJB:

        > ### Sample Code:  
        > *resource\_configuration.yml*
        > 
        > ```
        > ---
        > tomee/webapps/ROOT/META-INF/resources.xml:
        >   service_name_for_DefaultDB: di-core-hdi
        > ```


3.  Add the key values to be updated. You need to include the data source information to be updated in the **`manifest.yml`** file.

    -   Define the new service name for the look-up of the data source in a Web application:

        > ### Sample Code:  
        > *manifest.yml*
        > 
        > ```
        > 
        > env:
        >   TARGET_RUNTIME: tomee
        >   JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomee/webapps/ROOT/WEB-INF/resources.xml': {'service_name_for_DefaultDB' : 'my-local-di-core-hdi'}]"
        > ```

    -   Define the new service name for the look-up of the data source in an EJB:

        > ### Sample Code:  
        > *manifest.yml*
        > 
        > ```
        > 
        > env:
        >   TARGET_RUNTIME: tomee
        >   JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomee/webapps/ROOT/META-INF/resources.xml':{'service_name_for_DefaultDB' : 'my-local-di-core-hdi'}]"
        > ```





<a name="loio03cfb10c5b2042bd9cc0a1bc6bc6ba92__result_hvq_wz5_2fb"/>

## Results

As a result of this configuration, when the application starts, the *com.sap.xs.jdbc.datasource.TomEEDataSourceFactory* factory takes the parameters bound to the **my-local-di-core-hdi** service from the environment, creates a data source, and binds it under `jdbc/DefaultDB`. The application then uses the Java Naming and Directory Interface \(JNDI\) to look up how to connect with the database.

**Related Information**  


[SAP HANA HDI Data Source Usage](sap-hana-hdi-data-source-usage-c9d288e.md "If you want your Java application to consume SAP HANA Database (for example, to use an HDI container), follow the steps below.")

[Database Connection Configuration Details](database-connection-configuration-details-f0d2d05.md "Define details of the database connection used by your Java Web Application running on SAP BTP, Cloud Foundry with SAP Java Buildpack.")

