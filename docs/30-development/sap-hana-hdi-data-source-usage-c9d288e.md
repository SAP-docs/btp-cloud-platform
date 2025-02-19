<!-- loioc9d288e60f0942208c76bd99905dda15 -->

# SAP HANA HDI Data Source Usage

If you want your Java application to consume SAP HANA Database \(for example, to use an HDI container\), follow the steps below.



## Procedure

1.  Create a service instance for the HDI container, using the `cf create-service` command.

    ```
    cf create-service hana hdi-shared my-hdi-container
    ```

2.  Bind the service instance to a Java application.

    Specify the service instance in the Java application's deployment *manifest.yml* file.

    > ### Sample Code:  
    > ```
    > 
    > services: 
    > - my-hdi-container
    > ```

3.  Add a resource reference XML block. Its technical name must be the same as the name of the service instance.

    > ### Sample Code:  
    > ```
    > 
    > <resource-ref>
    >   <res-ref-name>jdbc/my-hdi-container</res-ref-name>
    >   <res-type>javax.sql.DataSource</res-type>
    > </resource-ref>
    > ```

    Add this resource reference to the following files, respectively:

    -   For Tomcat: **`web.xml`** and **`context.xml`**

    -   For TomEE: **`web.xml`** and **`resource.xml`**


4.  Look up the data source in your code.

    You can find the reference to the data source in two ways – by using annotations or with JNDI look-up. Add the relevant code to your Java servlet:

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



**Related Information**  


[SAP HDI Containers](https://help.sap.com/docs/SAP_HANA_PLATFORM/4505d0bdaf4948449b7f7379d24d0f0d/e28abca91a004683845805efc2bf967c.html?version=latest)

[Set Up a Schema or an HDI Container \(Cloud Foundry\)](https://help.sap.com/docs/hana-cloud/sap-hana-cloud-getting-started-guide/set-up-schema-or-hdi-container-cloud-foundry)

