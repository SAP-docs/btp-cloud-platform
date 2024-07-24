<!-- loio03cfb10c5b2042bd9cc0a1bc6bc6ba92 -->

# Configure a Database Connection for the TomEE 7 Application Container



<a name="loio03cfb10c5b2042bd9cc0a1bc6bc6ba92__steps_nqh_bx5_2fb"/>

## Procedure

1.  Create a `resources.xml` file.

    > ### Note:  
    > If the data source is to be used from a Web application, you have to create the file inside the `WEB-INF/` directory.
    > 
    > If the data source is to be used from Enterprise JavaBeans \(EJBs\), you have to create the file inside the `META-INF/` directory.

    The `resources.xml` file has to be inside the application's WAR file and has to contain information about the data source to be used.

    ```
    <?xml version='1.0' encoding='utf-8'?>
    
    <resources>
     <Resource id="jdbc/DefaultDB" provider="xs.openejb:XS Default JDBC Database" type="javax.sql.DataSource" >
        service=${service_name_for_DefaultDB}
      </Resource>
    </resources>
    ```

2.  Add the default keys and their values.

    You need to include the data source information in `META-INF/sap_java_buildpack/config/resource_configuration.yml` of the WAR file.

    > ### Sample Code:  
    > Defining a default service in resource\_configuration.yml for a Web application
    > 
    > ```
    > ---
    > tomee7/webapps/ROOT/WEB-INF/resources.xml:
    >   service_name_for_DefaultDB: di-core-hdi
    > ```

    > ### Sample Code:  
    > Defining a default service in resource\_configuration.yml for an EJB
    > 
    > ```
    > ---
    > tomee7/webapps/ROOT/META-INF/resources.xml:
    >   service_name_for_DefaultDB: di-core-hdi
    > ```

3.  Add the key values to be updated.

    Include the data source information to be updated in the `manifest.yml` file.

    > ### Sample Code:  
    > Defining a new service for the look-up of the data source in a Web application
    > 
    > ```
    > env:
    >   TARGET_RUNTIME: tomee7
    >   JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomee7/webapps/ROOT/WEB-INF/resources.xml': {'service_name_for_DefaultDB' : 'my-local-special-di-core-hdi'}]"
    > ```

    > ### Sample Code:  
    > Defining a new service for the look-up of the data source in an EJB
    > 
    > ```
    > env:
    >   TARGET_RUNTIME: tomee7
    >   JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomee7/webapps/ROOT/META-INF/resources.xml':{'service_name_for_DefaultDB' : 'my-local-special-di-core-hdi'}]"
    > ```




<a name="loio03cfb10c5b2042bd9cc0a1bc6bc6ba92__result_hvq_wz5_2fb"/>

## Results

As a result of this configuration, when the application starts, the *com.sap.xs.jdbc.datasource.TomEEDataSourceFactory* factory takes the parameters bound to the my-local-special-di-core-hdi service from the environment, creates a data source, and binds it under `jdbc/DefaultDB`. The application then uses the Java Naming and Directory Interface \(JNDI\) to look up how to connect with the database.

**Related Information**  


[SAP HANA HDI Data Source Usage](sap-hana-hdi-data-source-usage-c9d288e.md "If you want your Java application to consume SAP HANA Database (for example, to use an HDI container), follow the steps below.")

[Database Connection Configuration Details](database-connection-configuration-details-f0d2d05.md "Define details of the database connection used by your Java Web Application running on SAP BTP, Cloud Foundry with SAP Java Buildpack.")

[Configuring a Database Connection](configuring-a-database-connection-7568c3d.md)

