<!-- loioa04a06d65a164153919ca202d2a57e34 -->

# Connect an Application to PostgreSQL via TLS Certificate



<a name="loioa04a06d65a164153919ca202d2a57e34__prereq_nb1_dps_dgc"/>

## Prerequisites

You need to have a Java application created in the SAP BTP, Cloud Foundry environment.



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

5.  Run the following command:

    ```
    cf env myapp
    ```

    **Output:**

    ```
    
    <path>\java-tutorial>cf env myapp
    ...
    System-Provided:
    VCAP_SERVICES: {
      "postgresql-db": [
        {
          "binding_guid": "123456789-aaaa-1111-cccc-987654321",
          "binding_name": null,
          "credentials": {
            "dbname": "...",
            "hostname": "...",
            "password": "...",
            "port": "1234",
            "sslcert": "-----BEGIN CERTIFICATE-----\nMIID/zCCAuegAwIBAg... \...UbBiKPA7lVVhre\n-----END CERTIFICATE-----",
            "sslrootcert": "-----BEGIN CERTIFICATE-----\nMIID/zCCAuegAwIBAg... \...FDQnKF5OxwbAgip42CD
    
    ```

6.  In the "**`postgresql-db`**" part of the VCAP\_SERVICES section, check which of the following SSL certificates are available:

    -   `sslcert`

    -   `sslkey`

    -   `sslrootcert`


    In the exemplary output above, certificates **`sslcert`** and **`sslrootcert`** are displayed.

7.  Check if the corresponding certificate names are available in directory `~./postgresql` directory:

    -   **`postgresql.crt`**
    -   **`postgresql.key`**
    -   **`root.crt`**

    > ### Restriction:  
    > All these certificates are installed by default if you're using GCP.
    > 
    > If you're using a different IaaS provider, only the **`root.crt`** certificate will be available.

    See also: [Using Secure Socket Layer \(SSL\) Encryption for PostgreSQL DB Instances](https://help.sap.com/docs/postgresql-on-sap-btp/postgresql-on-sap-btp-hyperscaler-option/using-secure-socket-layer-ssl-encryption-for-postgresql-db-instances)


