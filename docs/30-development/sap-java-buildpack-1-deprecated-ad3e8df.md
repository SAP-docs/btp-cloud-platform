<!-- loioad3e8dfdbaad423e96ca875a4cd36f61 -->

# SAP Java Buildpack 1 – DEPRECATED!

SAP Java Buildpack 1 is a Cloud Foundry buildpack for running JVM-based applications.

This buildpack supports Java 8, 11, and 17, as well as the following runtimes:

-   [TomEE 7](tomee-7-79c039a.md)

-   [Tomcat 9](tomcat-9-ddfc101.md)

-   [Java Main](java-main-8a1786a.md)


> ### Caution:  
> Bear in mind that SAP Java Buildpack 1 has been deprecated and is going to be **removed** from SAP BTP, Cloud Foundry environment on **December 31, 2025**!
> 
> For more information, see:
> 
> -   [Release Notes - April 3, 2025](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?Component=SAP+Java+Buildpack&Valid_as_Of=2025-04-01:2025-04-05&locale=en-US&version=Cloud)
> -   [Release Notes – October 1, 2025](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?Component=SAP+Java+Buildpack&Valid_as_Of=2025-09-28:2025-10-03)
> -   [Release Notes – December 31, 2025](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?Component=SAP+Java+Buildpack&Valid_as_Of=2025-10-01:2025-12-31)



<a name="loioad3e8dfdbaad423e96ca875a4cd36f61__section_xxx_4w3_t2b"/>

## Usage

To use this buildpack, specify its name when deploying a Java application to the SAP BTP, Cloud Foundry environment. You can do it the following ways:

-   Specify it directly in the `cf push` command:

    ```
    cf push -f <PATH_TO_APP_MANIFEST> -b sap_java_buildpack
    ```


-   Specify it in the **`manifest.yml`** file of your application by using the `buildpacks` attribute:

    ```
    
    ---
    applications:
    - name: <APP_NAME>
      memory: 512M
      buildpacks:
      - sap_java_buildpack
      ...
      env:
        TARGET_RUNTIME: tomcat
    ```

    Then, you can deploy the application like this:

    ```
    cf push <app_name>
    ```

-   Specify it in the **`mtad.yaml`** deployment descriptor file \(for multi-target applications\) by using the `buildpack` attribute:

    ```
    
    ...
    modules:
      - name: <APP_NAME>
        type: java.tomcat
        path: <path_to_archive>
        properties:
          ...
        parameters:
          ...
          memory: 512M
          buildpack: sap_java_buildpack
    ...
    ```

    Then, you can deploy the application like this:

    ```
    cf push <app_name>
    ```




<a name="loioad3e8dfdbaad423e96ca875a4cd36f61__section_czc_1hd_kgb"/>

## Buildpack Versions

The SAP BTP, Cloud Foundry environment provides four versions of SAP Java Buildpack 1 as part of its system buildpacks:

-   *sap\_java\_buildpack* – Holds the latest available version of SAP Java Buildpack 1. All new features and fixes are provided with this version.

-   *sap\_java\_buildpack\_<version\_latest\>* – Holds the latest available version of SAP Java Buildpack 1. It's available for a limited timeframe \(4 to 6 weeks\).

-   *sap\_java\_buildpack\_<version\_previous\>* – This version used to be latest in the previous update of the SAP BTP, Cloud Foundry environment. It's available for a limited timeframe \(4 to 6 weeks\).

-   *sap\_java\_buildpack\_<version\_before\_previous\>* – This version used to be latest before two updates of the SAP BTP, Cloud Foundry environment. It's available for a limited timeframe \(4 to 6 weeks\).


To check these versions, proceed as follows:

1.  Log in to a particular SAP BTP region and subaccount. For example, if your region is **eu10**, run:

    ```
    cf api https://api.cf.eu10.hana.ondemand.com
    ```

2.  Then run:

    ```
    cf buildpacks
    ```




### How to use versions of SAP Java Buildpack 1?

-   **Option 1:** Use the default one – *sap\_java\_buildpack* 

    You take advantage of all latest features and fixes in SAP Java Buildpack 1. This way, it's guaranteed that the buildpack is always available. The drawback in this case is the limited time for adoption, if it's needed. In such a scenario, applications can fall back to an older version temporarily to avoid any downtime.

-   **Option 2:** Set a particular version – *sap\_java\_buildpack\_<version\_suffix\>*

    Bear in mind that this version will only exist for a limited amount of time. This may lead to the situation where application restage is failing because the used version of the buildpack is no longer available. To avoid this, we recommend that you follow the updates of the buildpack and test your applications with its latest version. Developers should never allow their applications to run on an outdated buildpack version.


**Example:**

Let's say that the latest version of SAP Java Buildpack 1 is **1.114.0**. Then, the output of the `cf buildpacks` command would be:

```

buildpack                position    enabled     locked    filename

sap_java_buildpack           1         true      false     sap_java_buildpack-v1.114.0.zip
sap_java_buildpack_1_114     2         true      false     sap_java_buildpack-v1.114.0.zip
sap_java_buildpack_1_113     3         true      false     sap_java_buildpack-v1.113.0.zip
sap_java_buildpack_1_112     4         true      false     sap_java_buildpack-v1.112.0.zip
```

When SAP Java Buildpack 1 is updated on the SAP BTP, Cloud Foundry environment from version **1.114.0** to **1.115.0**, the list will change to:

```

buildpack                position    enabled     locked    filename

sap_java_buildpack           1         true      false     sap_java_buildpack-v1.115.0.zip
sap_java_buildpack_1_115     2         true      false     sap_java_buildpack-v1.115.0.zip
sap_java_buildpack_1_114     3         true      false     sap_java_buildpack-v1.114.0.zip
sap_java_buildpack_1_113     4         true      false     sap_java_buildpack-v1.113.0.zip
```

This means that *sap\_java\_buildpack\_1\_112* will no longer be available for applications.

> ### Note:  
> No fixes will be provided to older versions of the buildpack. Fixes, including security ones, will be part of the latest version.



### How to switch to a specific buildpack version?

To use *sap\_java\_buildpack\_<version\_suffix\>*, specify its name when pushing an application to SAP BTP, Cloud Foundry environment:

```
cf push -f <PATH_TO_APP_MANIFEST> -b sap_java_buildpack_1_115
```

Alternatively, you can specify the buildpack in the `manifest.yml` file.

For example:

```
---
applications:
- name: myapp
  memory: 128M
  path: ./target/myapp.war
  instances: 1
  buildpacks:
  - sap_java_buildpack_1_115
```

You can do the same in the `mtad.yml` of your **mtar** archive:

```
...
modules:
  - name: myapp
    type: java.tomcat
    path: ./target/myapp.war
    properties:
      ...
    parameters:
      ...
      memory: 512M
      buildpack: sap_java_buildpack_1_115
...
```



<a name="loioad3e8dfdbaad423e96ca875a4cd36f61__section_dvg_kcz_vtb"/>

## Supported Java Versions

SAP Java Buildpack 1 \(`sap_java_buildpack`\) supports the following Java versions:

-   Java **8** – default version when you use SAP JVM \(*it provides a JRE and JDK with Java 8*\)
-   Java **11** – default version when you use SapMachine \(*it provides a JRE with Java 11*\)
-   Java **17** – possible version when you use SapMachine \(*it provides a JRE with Java 17*\)

To learn how to configure your application to use SapMachine JRE and JDK, see: [SapMachine](sapmachine-785d6b3.md)



<a name="loioad3e8dfdbaad423e96ca875a4cd36f61__section_yxx_4w3_t2b"/>

## Components

SAP Java Buildpack 1 provides the following components in the application container \(`<APP_ROOT_DIR>/app/META-INF/.sap_java_buildpack`\):

-   Runtimes – [Tomcat 9](tomcat-9-ddfc101.md), [TomEE 7](tomee-7-79c039a.md), and [Java Main](java-main-8a1786a.md)

-   [SapMachine](sapmachine-785d6b3.md)

-   [Memory Calculator V2](memory-calculator-v2-8eef959.md) - default

-   [Memory Calculator V1 \(SAP JVM Memory Calculator\)](memory-calculator-v1-sap-jvm-memory-calculator-c1059e0.md) - optional

-   [SAP BTP Security Services Integration Libraries](https://github.com/SAP/cloud-security-services-integration-library) – version 2.x


To check all the components regularly updated in the SAP Java Buildpack 1.x releases, see: [SAP Java Buildpack BOM](https://mvnrepository.com/artifact/com.sap.cloud.sjb.cf/sap-java-buildpack-bom)



<a name="loioad3e8dfdbaad423e96ca875a4cd36f61__section_wg4_djf_krb"/>

## What's New

To see the latest news and updates about SAP Java Buildpack 1, regularly check the release notes on the [What's New portal](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?locale=en-US&Component=SAP%20Java%20Buildpack).



<a name="loioad3e8dfdbaad423e96ca875a4cd36f61__section_cc2_qzf_hvb"/>

## Troubleshooting

If you encounter an issue while using SAP Java Buildpack 1, you can:

-   Search for your problem in our [Troubleshooting](sap-java-buildpack-ee609aa.md) section.

-   Create an incident for your specific problem, using support component **BC-CP-CF-BLDP**. To provide the necessary details, use the following template: [Initial Problem-Related Data](troubleshooting-073b7fc.md) 


See also:

-   SAP Note: [3261748](https://me.sap.com/notes/3261748) *SapMachine is replacing OpenJDK 11 & 17 in java\_buildpack*
-   SAP Note: [3214025](https://me.sap.com/notes/3214025) *Migrating Java Applications from TomEE 1.7 to TomEE 7*



<a name="loioad3e8dfdbaad423e96ca875a4cd36f61__section_ugc_sbl_15b"/>

## Java Tutorial

The following tutorial will guide you through creating a Java application in Cloud Foundry Command Line Interface \(cf CLI\), consuming Cloud Foundry services, and setting up authentication and authorization checks. See: [Create an Application with SAP Java Buildpack](https://developers.sap.com/tutorials/btp-cf-buildpacks-java-create.html)

