<!-- loioc893e9c7d05e4cca8151a5c3d87ec6ce -->

# Resource Configuration

You can configure your [application container](runtimes-and-containers-83d2416.md) by using text configuration files.

For example:

-   `conf/tomee7.xml`

-   `conf/tomee.xml`

-   `conf/server.xml`

-   `conf/logging.properties`


Resource configuration feature of SAP Java Buildpack provides means for changing parameterized values in all text files \(part of the application container or part of the application files\) during staging.

Files can contain multiple key-value pairs containing placeholders, marked as **`${propname}`**. To prevent undesired modifications, all files that can be changed must be explicitly listed by the application in a corresponding **`resource_configuration.yml`** file, along with the default values for all placeholders.



<a name="loioc893e9c7d05e4cca8151a5c3d87ec6ce__section_kbh_h5v_jcc"/>

## Template for `resource_configuration.yml`

```
---
filepath1:
  key1: value1
  key2: value2
filepath2:
  key1: value1
```

Depending on the SAP Java Buidlpack version \(1 or 2\), the `filepath1` must start with either **tomcat**, **tomee**, or **tomee7** to match the used application container, and should contain a subpath to a resource.

-   When changing parametrized values inside application files, the file path should look like this:

    `<application_container>/webapps/ROOT/<path_to_file_relative_to_application_root>`

-   When changing parametrized values in the configuration of an application container, the file path should look like this:

    `<application_container>/conf/<path_to_config_file>`




<a name="loioc893e9c7d05e4cca8151a5c3d87ec6ce__section_gd4_gtv_jcc"/>

## Example 1

You can create a `resource_configuration.yml` with the following content:

```

tomcat/webapps/ROOT/WEB-INF/mytextfile.txt:
  placeholder: "defaultValue"
tomcat/conf/server.xml:
  connector.maxThreads: 800

```



<a name="loioc893e9c7d05e4cca8151a5c3d87ec6ce__section_iq5_dtv_jcc"/>

## Example 2

1.  You have a given application with the following application files:

    ```
    
    src/
    	main/
    		java/
    		resources/
    		webapp/
    			META-INF/
    				sap_java_buildpack_jakarta/
    					config/
    						resource_configuration.yml
    			WEB-INF/
    				mytextfile.txt
    
    ```

2.  The content of `mytextfile.txt` is:

    ```
    My hometown is ${hometown}.
    ```

3.  The `resource_configuration.yml` looks like this:

    ```
    ---
    tomcat/webapps/ROOT/WEB-INF/mytextfile.txt:
      hometown: "London"
    ```

4.  After the application is staged, the content of `mytextfile.txt` will be:

    ```
    My hometown is London.
    ```




<a name="loioc893e9c7d05e4cca8151a5c3d87ec6ce__section_pwr_gtv_jcc"/>

## Example 3

The following example demonstrates how to provide values for placeholders during staging.

1.  Use the data from **Example 2** \(steps 1-3\).

2.  Then, in the `manifest.yml` file of the application, add the following environment variable:

    ```
    env:
      JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomcat/webapps/ROOT/WEB-INF/mytextfile.txt': {'hometown':"Paris"}]"
    ```

    This gives the possibility to provide values for placeholders that differ from the default ones provided in the example above.

3.  After staging of the application, the content of `mytextfile.txt` will be modified to:

    ```
    My hometown is Paris.
    ```


**Related Information**  


[Overriding Resources in Droplet](overriding-resources-in-droplet-0a34588.md "Applications can override resources in the droplet by placing directory files that have the same relative path as the droplet root.")

[Apache Tomcat 9: Configuration Reference](https://tomcat.apache.org/tomcat-9.0-doc/config/)

[Apache Tomcat 10: Configuration Reference](https://tomcat.apache.org/tomcat-10.0-doc/config/)

[Apache TomEE: Server Configuration](https://tomee.apache.org/latest/docs/admin/configuration/index.html)

