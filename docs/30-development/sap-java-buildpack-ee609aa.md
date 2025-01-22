<!-- loioee609aa3c1b44987af1ce7148fedf4e6 -->

# SAP Java Buildpack

This page provides solutions on known issues related to SAP Java Buildpack 1 and 2.

If you can't find a solution to your problem, create an incident to component **`BC-CP-CF-BLDP`**.



<a name="loioee609aa3c1b44987af1ce7148fedf4e6__section_tgz_java_aaa"/>

## Application Deployment on TomEE 1.7 Fails



### Problem

When trying to execute a Java application running on Apache TomEE 1.7, the following error appears:

```
SEVERE: Unhandled exception in Buildpack main method: None of the available runtimes [Tomee7, Tomcat, Java Main] supports the application in the specified path.
```



### Reason

Since **May 5, 2022**, Apache TomEE 1.x is no longer supported by SAP Java Buildpack 1 \(effective version `1.53.0`\). See: [Release Notes](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?Component=SAP%2520Java%2520Buildpack&Valid_as_Of=2022-01-01%253A2022-05-10&version=Cloud&locale=en-US)

You need to modify your Java applications to run on Apache TomEE 7 instead. To do that, follow the solution below.



### Solution

1.  Configure the `manifest.yml` file of your Java application:

    -   Make sure that the `buildpack` variable is set to **`sap_java_buildpack`**. If pinned to a particular version, it must be at least 1.53.0.

    -   For the TARGET\_RUNTIME variable, replace `tomee` with **`tomee7`**. To learn more, see [TomEE 7](https://help.sap.com/docs/btp/sap-business-technology-platform/tomee-7?version=Cloud).

        For example:

        ```
        
          ---
          applications:
          - name: myapp
            path: .\target\myapp.jar
            buildpacks: 
            - sap_java_buildpack
            . . .
            env:
              TARGET_RUNTIME: tomee7
              JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
        
        ```


2.  Check the information provided for Apache TomEE: [Migrate from TomEE 1 to TomEE 7](https://tomee.apache.org/tomee-7.1/docs/developer/migration/tomee-1-to-7.html)

3.  Besides the TARGET\_RUNTIME variable, additional setups are needed. Please follow the [guide](https://help.sap.com/docs/btp/sap-business-technology-platform/tomee-7?version=Cloud) for using TomEE 7.

4.  After applying the new change, if your application fails with an *OutOfMemoryError* exception, change your memory size configuration. See:

    [Memory Calculator V1](memory-calculator-v1-sap-jvm-memory-calculator-c1059e0.md)

    [XS Advanced Model: Memory Size Options](https://help.sap.com/docs/SAP_HANA_PLATFORM/4505d0bdaf4948449b7f7379d24d0f0d/5c253fd9539340369478809b3977be72.html)


