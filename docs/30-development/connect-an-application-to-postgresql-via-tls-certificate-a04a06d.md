<!-- loioa04a06d65a164153919ca202d2a57e34 -->

# Connect an Application to PostgreSQL via TLS Certificate



<a name="loioa04a06d65a164153919ca202d2a57e34__prereq_nb1_dps_dgc"/>

## Prerequisites

You need to have a Java application running on SAP BTP, Cloud Foundry environment.



## Context

Provide extra security for your Java application when connecting it to PostgreSQL by using a Transport Layer Security \(TLS\) certificate.



## Procedure

1.  Create a service instance of *PostgreSQL, Hyperscaler Option*. For example, use plan **standard** and instance name **mydb**. Run:

    ```
    cf create-service postgresql-db standard mydb
    ```

2.  Bind the new service instance to your application. To do that, add **mydb** in the `manifest.yml` file of your application:

    ```
    
    ---
    applications:
    - name: myapp
      memory: 512M 
      buildpacks:
      - sap_java_buildpack_jakarta
      services:
      - mydb
    ...
      env:
        TARGET_RUNTIME: tomcat
    ```

3.  Add environment parameter `USE_CERTS_WITH_POSTGRES` in the `manifest.yml` file. For example, set it to **verify-ca**:

    ```
    
    ---
    applications:
    - name: myapp
      memory: 512M 
      buildpacks:
      - sap_java_buildpack_jakarta
      services:
      - mydb
    ...
      env:
        USE_CERTS_WITH_POSTGRES: verify-ca
        TARGET_RUNTIME: tomcat
    ```

    To learn about all possible values, see [PostgreSQL: Protection Provided in Different Modes](https://www.postgresql.org/docs/17/libpq-ssl.html#LIBPQ-SSL-PROTECTION).

4.  Deploy your application. Run:

    ```
    cf push myapp
    ```

5.  Check if the following certificates are available in the PostgreSQL part of your VCAP\_SERVICES, related to the **`mydb`** service instance:

    -   `sslcert`
    -   `sslkey`
    -   `sslrootcert`

    To do that, run:

    ```
    cf env myapp
    ```

    You can find these certificates in directory `~./postgresql` with the following names, respectively:

    -   **`postgresql.crt`**
    -   **`postgresql.key`**
    -   **`root.crt`**

    > ### Tip:  
    > If you're using GCP, all these certificates are installed by default. If you're using a different IaaS provider, you need to add the missing ones, if any.


