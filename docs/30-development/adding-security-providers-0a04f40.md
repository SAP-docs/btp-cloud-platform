<!-- loio0a04f40b44894ad6ba1aeba96568e0b6 -->

# Adding Security Providers

You can add custom security providers to the `java.security` file at deploy time.

The SECURITY\_PROVIDERS mechanism supports adding one or more providers, with an explicit priority for each of them. Provider JARs can be supplied in two ways:

-   As standard project dependencies
-   Bundled inside the application



## Prerequisites

You have created and deployed a Jakarta-based application.



## Procedure

1.  Open your `manifest.yml` file.
2.  Add the SECURITY\_PROVIDERS entries by using the "`<index>|<value>`" format. You can add single or multiple ones, like this:

    -   Single provider: `SECURITY_PROVIDERS: "1|org.security.ProviderA"`

    -   Multiple providers: `SECURITY_PROVIDERS: "1|org.security.ProviderA 2|org.security.ProviderB"`


    > ### Example:  
    > ```
    > 
    > ---
    > applications:
    > - name: <APP_NAME>
    >   memory: 512M
    >   buildpacks:
    >   - sap_java_buildpack_jakarta
    >   ...
    >   env:
    >     TARGET_RUNTIME: tomcat
    >     SECURITY_PROVIDERS: "1|org.security.ProviderA 2|org.security.ProviderB"
    > ```

3.  Add the provider JARs. You can do this in two ways:
    -   Provided as normal application dependencies \(for example, via the `pom.xml` file\). SAP Java Buildpack will pick up those JARs from the application classpath.

        ```
        
        <dependencies>
          <dependency>
            <groupId>org.providerA</groupId>
            <artifactId>providerA</artifactId>
            <version>${providerA.version}</version>
          </dependency>
          <dependency>
        
            <groupId>org.providerB</groupId>
            <artifactId>providerB</artifactId>
            <version>${providerB.version}</version>
          </dependency>
        
        </dependencies>
        ```

    -   Bundled in the app resources. To do that, place the provider JARs under directory **`webapp/META-INF/.sap_java_buildpack/custom_security_providers`**, like this:

        ```
        
        ├── webap
        └──── META-INF
        │     └──── .sap_java_buildpack
        │         └──── custom_security_providers
        │             └──── providerA.jar
        |             └──── providerB.jar
        └──── WEB-INF
             └──── ...
        ```


4.  Deploy your application. To do that, run:

    ```
    cf push <APP_NAME>
    ```




## Result

The mechanism parses the SECURITY\_PROVIDERS value from the `manifest.yml` file and adds the listed providers to the **`java.security`** file in the specified priority order. It supports multiple providers and avoids duplicate entries due to unique provider class names.

