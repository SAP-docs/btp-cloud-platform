<!-- loiof0d2d059b43c48098772bd05d7c51d25 -->

# Database Connection Configuration Details

Define details of the database connection used by your Java Web Application running on SAP BTP, Cloud Foundry with SAP Java Buildpack.



<a name="loiof0d2d059b43c48098772bd05d7c51d25__section_i4y_pld_p2b"/>

## Configuration Files

To configure your application to establish a connection to the SAP HANA database, you must specify details of the connection in a configuration file. For example, you must define the data source that the application will use to discover and look up data. The application then uses a Java Naming and Directory Interface \(JNDI\) to look up the specified data in the file.

The easiest way to define the required data source is to declare the keys for the data source in a resource file.

For the Tomcat application container, you can create a `context.xml` file in the `META-INF/` directory with the following content:

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

For the TomEE 7 application container, you can create a `resources.xml` file in the `WEB-INF/` directory with the following content:

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

The problem with this simple approach is that your WAR file cannot be signed, and any modifications can only be made in the WAR file. For this reason, it is recommended that you do not use the method in a production environment but rather take advantage of the [Resource Configuration](resource-configuration-c893e9c.md) feature of the SAP Java Buildpack. Use modification settings in `resource_configuration.yml` and `manifest.yml` as illustrated in the following examples.

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

The generic mechanism JBP\_CONFIG\_RESOURCE\_CONFIGURATION basically replaces the key values in the specified files. For this reason, if you use placeholders in the configuration files, it is important to ensure that you use unique names for the placeholders, see [Resource Configuration](resource-configuration-c893e9c.md).

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

