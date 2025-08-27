<!-- loioa04a06d65a164153919ca202d2a57e34 -->

# Connect an Application to PostgreSQL via TLS Certificate



<a name="loioa04a06d65a164153919ca202d2a57e34__prereq_nb1_dps_dgc"/>

## Prerequisites

You have a Java application created and deployed in an enterprise \(productive\) SAP BTP subaccount, in the SAP BTP, Cloud Foundry environment.

> ### Note:  
> This scenario is not applicable for SAP BTP trial accounts.



## Context

Use TLS certificates to provide extra security for your Java applications when connecting them to a PostgreSQL database.

The certificate names described below start with "ssl", which is correct as Transport Layer Security \(TLS\) is the advanced security successor of Secure Sockets Layer \(SSL\).



## Procedure

1.  Create a service instance of *PostgreSQL, Hyperscaler Option* with plan **`development`**. For example, let's create a service instance with name **mydb**. Run:

    ```
    cf create-service postgresql-db development mydb
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

4.  Before deploying your Java application, build your project again. Run:

    ```
    mvn clean install
    ```

5.  Deploy your application. Run:

    ```
    cf push myapp
    ```

6.  Check the contents of VCAP\_SERVICES. Run:

    ```
    cf env myapp
    ```

    From the output, go to the "**`postgresql-db`**" part of the VCAP\_SERVICES section and check which of the following SSL certificates are available:

    -   `sslcert`

    -   `sslkey`

    -   `sslrootcert`


    **Example Output:**

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

    In this example, certificates **`sslcert`** and **`sslrootcert`** are displayed.

7.  Check the contents of directory `./postgresql`. To do that:

    1.  Run: **`cf ssh myapp`**
    2.  Display a detailed directory listing. Run: **`ll`** 
    3.  List the contents of the `.postgresql` directory. Run: **`cd .postgresql`**

8.  Check which of the corresponding certificate names are listed in the `.postgresql` directory:

    -   **`postgresql.crt`**
    -   **`postgresql.key`**
    -   **`root.crt`**

    > ### Restriction:  
    > If you're using GCP, all these certificates are installed by default.
    > 
    > If you're using a different IaaS provider \(for example, AWS\), only the **`root.crt`** certificate will be available.


**Related Information**  


[Using Secure Socket Layer \(SSL\) Encryption for PostgreSQL DB Instances](https://help.sap.com/docs/postgresql-on-sap-btp/postgresql-on-sap-btp-hyperscaler-option/using-secure-socket-layer-ssl-encryption-for-postgresql-db-instances?version=Cloud)

