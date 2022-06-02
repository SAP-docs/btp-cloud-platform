<!-- loio820994a3e11d48dfaa3d3e251521a6ec -->

# Configure a Database Connection for the Tomcat Application Container



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

