<!-- loiocf1499da58144c94868ce12bd25a970f -->

# Configure a Database Connection for the TomEE Application Container



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


