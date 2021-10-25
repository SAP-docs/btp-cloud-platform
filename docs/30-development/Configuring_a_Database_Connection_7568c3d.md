<!-- loio7568c3d036f34a64bb6595b55805bffb -->

# Configuring a Database Connection



You can configure your application to use a database connection so that the application can persist its data. This configuration is applicable for the [Tomcat](Application_Containers_83d2416.md#loioddfc10180fe844049cc71f6989942dc2), [TomEE](Application_Containers_83d2416.md#loioa9590c2f5ebc4d1586d9f0f53a60cfdc) and [TomEE 7](Application_Containers_83d2416.md#loio79c039ab43b946a7b50c5d0326a3b40b) application containers.

-   [Configure a Database Connection for the Tomcat Application Container](Configuring_a_Database_Connection_7568c3d.md#loio820994a3e11d48dfaa3d3e251521a6ec)

-   [Configure a Database Connection for the TomEE Application Container](Configuring_a_Database_Connection_7568c3d.md#loiocf1499da58144c94868ce12bd25a970f)

-   [Configure a Database Connection for the TomEE 7 Application Container](Configuring_a_Database_Connection_7568c3d.md#loio03cfb10c5b2042bd9cc0a1bc6bc6ba92)

-   [Database Connection Configuration Details](Configuring_a_Database_Connection_7568c3d.md#loiof0d2d059b43c48098772bd05d7c51d25)

-   [SAP HANA HDI Data Source Usage](Configuring_a_Database_Connection_7568c3d.md#loioc9d288e60f0942208c76bd99905dda15)


 <a name="loio820994a3e11d48dfaa3d3e251521a6ec"/>

<!-- loio820994a3e11d48dfaa3d3e251521a6ec -->

## Configure a Database Connection for the Tomcat Application Container



## Procedure

1.  Create a `context.xml` file.

    The `context.xml` file has to be inside the `META_INF/` folder of the application WAR file and has to contain information about the data source to be used.

    ```
    <?xml version='1.0' encoding='utf-8'?>
    
    <Context>
     <Resource name="jdbc/DefaultDB"
        auth="Container"
        type="javax.sql.DataSource"
        factory="com.sap.xs.jdbc.datasource.tomcat.TomcatDataSourceFactory"
        service="${service_name_for_DefaultDB}"/>
    </Context>
    ```

2.  Add the default keys and their values.

    You need to include the data source information in `META-INF/sap_java_buildpack/config/resource_configuration.yml` of the WAR file.

    ```
    ---
     tomcat/webapps/ROOT/META-INF/context.xml:
      service_name_for_DefaultDB: di-core-hdi
    ```

3.  Add the key values to be updated.

    You include the data source information to be updated in `manifest.yml`.

    ```
    env:
      JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomcat/webapps/ROOT/META-INF/context.xml': {'service_name_for_DefaultDB' : 'my-local-special-di-core-hdi'}]"
    ```




<a name="loio820994a3e11d48dfaa3d3e251521a6ec__result_plz_bld_p2b"/>

## Results

When the application starts, the factory named `com.sap.xs.jdbc.datasource.TomcatDataSourceFactory` takes the parameters bound for service *my-local-special-di-core-hdi* from the environment, creates a data source, and binds it under `jdbc/DefaultDB`. The application then uses the Java Naming and Directory Interface \(JNDI\) to look up how to connect with the database.

 <a name="loiocf1499da58144c94868ce12bd25a970f"/>

<!-- loiocf1499da58144c94868ce12bd25a970f -->

## Configure a Database Connection for the TomEE Application Container



<a name="loiocf1499da58144c94868ce12bd25a970f__steps_jyv_gld_p2b"/>

## Procedure

1.  Create a `resources.xml` file.

    The `resources.xml` file must be inside the application's `WEB-INF/` folder and must contain information about the data source to be used.

    ```
    <?xml version='1.0' encoding='utf-8'?>
    
    <resources>
    <Resource id="jdbc/DefaultDB" provider="xs.openejb:XS Default JDBC Database" type="javax.sql.DataSource" >
        service=${service_name_for_DefaultDB}
      </Resource>
    </resources> 
    ```

2.  Add the default keys and their values.

    The data source information must be included in the`META-INF/sap_java_buildpack/config/resource_configuration.yml` file.

    ```
    ---
    tomee/webapps/ROOT/WEB-INF/resources.xml:
      service_name_for_DefaultDB: di-core-hdi
    ```

3.  Add the key values to be updated.

    Include the data source information to be updated in the `manifest.yml` file.

    ```
    env:
      TARGET_RUNTIME: tomee
      JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomee/webapps/ROOT/WEB-INF/resources.xml': {'service_name_for_DefaultDB' : 'my-local-special-di-core-hdi'}]"
    ```


 <a name="loio03cfb10c5b2042bd9cc0a1bc6bc6ba92"/>

<!-- loio03cfb10c5b2042bd9cc0a1bc6bc6ba92 -->

## Configure a Database Connection for the TomEE 7 Application Container



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


[SAP HANA HDI Data Source Usage](Configuring_a_Database_Connection_7568c3d.md#loioc9d288e60f0942208c76bd99905dda15)

[Database Connection Configuration Details](Configuring_a_Database_Connection_7568c3d.md#loiof0d2d059b43c48098772bd05d7c51d25 "Define details of the database connection used by your Java Web Application running on Cloud Foundry Environment with the SAP Java Buildpack.")

[Configuring a Database Connection](Configuring_a_Database_Connection_7568c3d.md#loio7568c3d036f34a64bb6595b55805bffb "Define details of the database connection used by your Java Web Application running on Cloud Foundry Environment with the SAP Java Buildpack.")

 <a name="loiof0d2d059b43c48098772bd05d7c51d25"/>

<!-- loiof0d2d059b43c48098772bd05d7c51d25 -->

## Database Connection Configuration Details

Define details of the database connection used by your Java Web Application running on Cloud Foundry Environment with the SAP Java Buildpack.



<a name="loiof0d2d059b43c48098772bd05d7c51d25__section_i4y_pld_p2b"/>

## Configuration Files

To configure your application to establish a connection to the SAP HANA database, you must specify details of the connection in a configuration file. For example, you must define the data source that the application will use to discover and look up data. The application then uses a Java Naming and Directory Interface \(JNDI\) to look up the specified data in the file.

The easiest way to define the required data source is to declare the keys for the data source in a resource file.

For the Tomcat Application Container, you can create a `context.xml` file in the `META-INF/` directory with the following content:

> ### Sample Code:  
> context.xml
> 
> ```
> <?xml version='1.0' encoding='utf-8'?>
> <Context>
>  <Resource name="jdbc/DefaultDB"
>     auth="Container"
>     type="javax.sql.DataSource"
>     factory="com.sap.xs.jdbc.datasource.tomcat.TomcatDataSourceFactory"
>     service="di-core-hdi"/>
> </Context>
> ```

For the TomEE Application Container, you can create a `resources.xml` file in the `WEB-INF/` directory with the following content:

> ### Sample Code:  
> resources.xml
> 
> ```
> <?xml version='1.0' encoding='utf-8'?> 
> <resources>
>  <Resource id="jdbc/DefaultDB" provider="xs.openejb:XS Default JDBC Database" type="javax.sql.DataSource" >
>     service=di-core-hdi
>  </Resource>
> </resources>
> ```

The problem with this simple approach is that your WAR file cannot be signed, and any modifications can only be made in the WAR file. For this reason, it is recommended that you do not use the method in a production environment but rather take advantage of the [Resource Configuration](Resource_Configuration_c893e9c.md) feature of the SAP Java Buildpack. Use modification settings in `resource_configuration.yml` and `manifest.yml` as illustrated in the following examples.

Defining a default service in `resource_configuration.yml`.

> ### Sample Code:  
> resource\_configuration.yml
> 
> ```
> ---
> tomcat/webapps/ROOT/META-INF/context.xml:
>   service_name_for_DefaultDB: di-core-hdi
> ```

Specifying a default name for a service is useful \(for example, for automation purposes\) only if you are sure there can be no conflict with other names. For this reason, it is recommended that you include a helpful and descriptive error message instead of a default value. That way the error message will be part of an exception triggered when the data source is initialized, which helps troubleshooting.

Sample `resource_configuration.yml`.

> ### Sample Code:  
> ```
> ---
> tomcat/webapps/ROOT/META-INF/context.xml:
>   service_name_for_DefaultDB: Specify the service name for Default DB in manifest.yml via "JBP_CONFIG_RESOURCE_CONFIGURATION"..
> ```



<a name="loiof0d2d059b43c48098772bd05d7c51d25__section_zq3_qld_p2b"/>

## Placeholders

The generic mechanism JBP\_CONFIG\_RESOURCE\_CONFIGURATION basically replaces the key values in the specified files. For this reason, if you use placeholders in the configuration files, it is important to ensure that you use unique names for the placeholders, see [Resource Configuration](Resource_Configuration_c893e9c.md).

Sample `context.xml`.

> ### Sample Code:  
> context.xml
> 
> ```
> <?xml version='1.0' encoding='utf-8'?>
> 
> <Context>
>  <Resource name="jdbc/DefaultDB"
>   auth="Container"
>   type="javax.sql.DataSource"
>   description="Datasource for general functionality"
>   factory="com.sap.xs.jdbc.datasource.tomcat.TomcatDataSourceFactory"
>   service="${service_name_for_DefaultDB}"
>   maxActive="${max_Active_Connections_For_DefaultDB}"  />   
> 
>  <Resource name="jdbc/DefaultXADB"
>   auth="Container"
>   type="javax.sql.XADataSource"
>   description="Datasource for functionality requiring more than one transactional resource"
>   factory="com.sap.xs.jdbc.datasource.tomcat.TomcatDataSourceFactory"
>   service="${service_name_for_DefaultXADB}"
>   maxActive="${max_Active_Connections_For_DefaultXADB}" />
> </Context>
> ```

The names of the defined placeholders are also used in the other resource files.

Sample `resource_configuration.yml`.

> ### Sample Code:  
> resource\_configuration.yml
> 
> ```
> ---
> tomcat/webapps/ROOT/META-INF/context.xml:
>   service_name_for_DefaultDB: di-core-hdi
>   max_Active_Connections_For_DefaultDB: 100
>   service_name_for_DefaultDB: di-core-hdi-xa
>   max_Active_Connections_For_DefaultXADB: 100
>   
> 
> env:
>   JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomcat/webapps/ROOT/META-INF/context.xml': {'service_name_for_DefaultDB' : 'my-local-special-di-core-hdi' , 'max_Active_Connections_For_DefaultDB' : '30', 'service_name_for_DefaultXADB' : 'my-local-special-xa-di-core-hdi' , 'max_Active_Connections_For_DefaultXADB' : '20'  }]"
> ```

Sample `manifest.yml`.

> ### Sample Code:  
> manifest.yml
> 
> ```
> env:
>   JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomcat/webapps/ROOT/META-INF/context.xml': {'service_name_for_DefaultDB' : 'my-local-special-di-core-hdi' , 'max_Active_Connections_For_DefaultDB' : '30', 'service_name_for_DefaultXADB' : 'my-local-special-xa-di-core-hdi' , 'max_Active_Connections_For_DefaultXADB' : '20'  }]"
> ```

 <a name="loioc9d288e60f0942208c76bd99905dda15"/>

<!-- loioc9d288e60f0942208c76bd99905dda15 -->

## SAP HANA HDI Data Source Usage



## Procedure

1.  Create a service instance for the HDI container, using the `cf create-service` command.

    ```
    cf create-service hana hdi-shared my-hdi-container
    ```

2.  Bind the service instance to a Java application.

    Specify the service instance in the Java application's deployment manifest file.

    > ### Sample Code:  
    > manifest.yml
    > 
    > ```
    > services: 
    > - my-hdi-container
    > ```

3.  Add the resource reference to the `web.xml` file, which must have the name of the service instance.

    > ### Sample Code:  
    > web.xml
    > 
    > ```
    > <resource-ref>
    >   <res-ref-name>jdbc/my-hdi-container</res-ref-name>
    >   <res-type>javax.sql.DataSource</res-type>
    > </resource-ref>
    > ```

4.  Look up the data source in your code.

    You can find the reference to the data source in the following ways:

    -   Annotations

        ```
        @Resource(name = "jdbc/my-hdi-container")
        private DataSource ds;
        ```

    -   Java Naming and Directory Interface \(JNDI\) look-up

        ```
        Context ctx = new InitialContext(); 
        return (DataSource) ctx.lookup("java:comp/env/jdbc/my-hdi-container");
        ```



