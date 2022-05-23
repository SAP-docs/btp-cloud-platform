<!-- loioc9d288e60f0942208c76bd99905dda15 -->

# SAP HANA HDI Data Source Usage



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



