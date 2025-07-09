<!-- loio7eb922a1668a435d8bd681263e0be12e -->

# Logging and Tracing



<a name="loio7eb922a1668a435d8bd681263e0be12e__context_nwf_1vd_p2b"/>

## Context

SAP Java Buildpack integrates the [Cloud Foundry Java Logging Support](https://github.com/SAP/cf-java-logging-support) libraries, allowing applications to produce logs in JSON format that can be parsed by the SAP Application Logging service for SAP BTP.



## Procedure

1.  Bind your application to an [SAP Application Logging](https://help.sap.com/docs/application-logging-service/sap-application-logging-service/what-is-sap-application-logging-service?version=Cloud) service instance. This way, you can produce application logs and forward them to a central application logging stack.

2.  If you want to generate request metrics for applications based on Tomcat or TomEE, add *com.sap.hcp.cf.logging.servlet.filter.RequestLoggingFilter* to the **`web.xml`** file.

    ```
    <filter-name>request-logging</filter-name>
       <filter-class>com.sap.hcp.cf.logging.servlet.filter.RequestLoggingFilter</filter-class>
    </filter>
    <filter-mapping>
       <filter-name>request-logging</filter-name>
       <url-pattern>/*</url-pattern>
    </filter-mapping>
    ```

    > ### Note:  
    > The default log level of *com.sap.hcp.cf.logging.servlet.filter.RequestLoggingFilter* is set to INFO.

3.  Check the logs of the application.

    If the binding of your application to the SAP Application Logging service is successful, the application logs can be found on **`https://logs.cf.<SAP_BTP_region>`**. To request the logs of your application, run:

    ```
    cf logs <app_name> --recent
    ```

4.  \(Optional\) Change the log level of a logging location. You can do this in two ways - before and during application deploy.

    -   Change the log level before deploy, by using a file. You need to restart your application after that. Use cases:

        -   Standard applications based on Tomcat or TomEE – configure the SET\_LOGGING\_LEVEL environment variable in the **`manifest.yml`** file. For example:

            ```
            
            env:
              SET_LOGGING_LEVEL: '{com.sap.sample.java.LogInfo: INFO, com.sap.sample.java.LogWarn: WARN}'
            ```

        -   Standard applications based on Java Main – create a **`logback.xml`** file in directory `src/main/resources`. For example:

            ```
            
            <configuration>
              <!-- Console appender -->
              <appender name="STDOUT" class="ch.qos.logback.core.ConsoleAppender">
                <encoder>
                  <pattern>%d{HH:mm:ss.SSS} [%thread] %-5level %logger{36} - %msg%n</pattern>
                </encoder>
              </appender>
            
              <!-- Set root log level -->
              <root level="DEBUG">
                <appender-ref ref="STDOUT" />
              </root>
            
              <!-- Optional: package-specific logging -->
              <logger name="org.example.Main" level="ERROR"/>
            </configuration>
            ```

        -   Spring Boot applications based on Java Main. Their default log configuration provides messages of levels ERROR, WARN, and INFO. To enable other log levels, for example DEBUG, create a file **`application.properties`** in directory `/src/main/resources/` and add the following line:

            ```
            
            logging.level.root=DEBUG
            ```

            To enable DEBUG logging for a particular class only, you can do so by specifying the fully qualified class name:

            ```
            
            logging.level.com.mypackage.MySpecificClass=DEBUG
            ```

            > ### Tip:  
            > If you use a Spring Boot generator \(for example [Spring Initializr](https://start.spring.io)\), the file directory `/src/main/resources/application.properties` is automatically created for you.


    -   Change the log level for any Java application in real time \(during deploy\), by using command: **`cf set-logging-level <app-name> <java-class> <level>`** 

        The changes will be applied immediately – no need to restart your application. For example:

        ```
        cf set-logging-level myapp123 com.sap.sample.java.LogWarn WARN
        ```


5.  \(Optional\) Check the audit logs.

    Changing the logging level of your application \(by using the **`set-logging-level`** command\) can be tracked in the audit log server. To enable audit logging, bind your Java application to an Audit Log service instance, with plan **oauth2**.

    **NOTE:** For SpringBoot applications based on Java Main, you also need to add the following dependencies in the **`pom.xml`** file:

    ```
    
    <dependency>
      <groupId>com.sap.cp.auditlog</groupId>
      <artifactId>audit-java-client-api</artifactId>
      <version>${com.sap.cp.auditlog.audit-java-client.version}</version>
    </dependency>
    										
    <dependency>
      <groupId>com.sap.cp.auditlog</groupId>
      <artifactId>audit-java-client-impl</artifactId>
      <version>${com.sap.cp.auditlog.audit-java-client.version}</version>
    </dependency>
    										
    <dependency>
      <groupId>com.sap.cloud.sjb</groupId>
      <artifactId>xs-env</artifactId>
      <version>${com.sap.cloud.sjb.xs-env.version}</version>
      <scope>runtime</scope>
    </dependency>
    ```


**Related Information**  


[Configure a Java Application for Logs and Traces](configure-a-java-application-for-logs-and-traces-5551c5e.md "Configure the collection of log and trace messages generated by a Java application in SAP BTP, Cloud Foundry.")

[SAP Application Logging Service for Cloud Foundry](https://help.sap.com/docs/APPLICATION_LOGGING/ee8e8a203e024bbb8c8c2d03fce527dc/68454d44ad41458788959485a24305e2.html?version=Cloud)

[Spring Boot: Logging](https://docs.spring.io/spring-boot/docs/2.1.8.RELEASE/reference/html/boot-features-logging.html)

