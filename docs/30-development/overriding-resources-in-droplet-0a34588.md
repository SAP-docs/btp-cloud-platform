<!-- loio0a345880fa6f4aa8b7c481ea5677d690 -->

# Overriding Resources in Droplet

Applications can override resources in the droplet by placing directory files that have the same relative path as the droplet root.

The following example shows how an application can override the default Tomcat's **server.xml** file in directory `META-INF/sap_java_buildpack/resources/`.



<a name="loio0a345880fa6f4aa8b7c481ea5677d690__section_sk1_2jj_3cc"/>

## Example

1.  You have the following file structure in your Java application:

    ```
    
    META-INF/
    - sap_java_buildpack/
      - resources/
        - tomcat/
          - conf/
            - server.xml/
    WEB-INF/
    
    ```

2.  After the application is built and deployed, this will result in the following file structure in the droplet:

    ```
    
    META-INF/
    - .sap_java_buildpack/
      - tomcat
        - conf/
          - server.xml
    WEB-INF/
    
    ```

3.  When the Tomcat container is started, the content of the **server.xml** file will come from the application.


This mechanism also allows adding new resources inside the droplet in their respective places, based on where the files are located under `META-INF/sap_java_buildpack/resources/`.

> ### Tip:  
> The overriding principle is applicable for both **sap\_java\_buildpack** and **sap\_java\_buildpack\_jakarta**.

**Related Information**  


[Resource Configuration](resource-configuration-c893e9c.md "You can configure your application container by using text configuration files.")

[Cloud Foundry component glossary](https://docs.cloudfoundry.org/concepts/glossary.html)

