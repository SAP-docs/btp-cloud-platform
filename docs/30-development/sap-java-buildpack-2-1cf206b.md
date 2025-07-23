<!-- loio1cf206b5ef7043b282ba87380fcfbfc1 -->

# SAP Java Buildpack 2

SAP Java Buildpack 2 is a Cloud Foundry buildpack for running SapMachine-based applications.

This buildpack supports Java 17 and 21, as well as the following runtimes:

-   [TomEE 10](tomee-10-66e808e.md)

-   [Tomcat 10](tomcat-10-97d0e34.md)

-   [Java Main](java-main-8a1786a.md)




<a name="loio1cf206b5ef7043b282ba87380fcfbfc1__section_xxx_444_t2b"/>

## Usage

To use this buildpack, specify its name when deploying a Jakarta-based application to the SAP BTP, Cloud Foundry environment. You can do it the following ways:

-   Specify it directly in the `cf push` command:

    ```
    cf push -f <PATH_TO_APP_MANIFEST> -b sap_java_buildpack_jakarta
    ```


-   Specify it in the **`manifest.yml`** file of your application by using the `buildpacks` attribute:

    ```
    
    ---
    applications:
    - name: <APP_NAME>
      memory: 512M
      buildpacks:
      - sap_java_buildpack_jakarta
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
          buildpack: sap_java_buildpack_jakarta
    ...
    ```

    Then, you can deploy the application like this:

    ```
    cf push <app_name>
    ```




<a name="loio1cf206b5ef7043b282ba87380fcfbfc1__section_czc_1hd_kgb"/>

## Buildpack Versioning

The SAP BTP, Cloud Foundry environment provides four versions of SAP Java Buildpack 2 as part of its system buildpacks:

-   *sap\_java\_buildpack\_jakarta* – Holds the latest available version of SAP Java Buildpack 2. All new features and fixes are provided with this version.

-   *sap\_java\_buildpack\_jakarta\_<version\_latest\>* – Holds the latest available version of SAP Java Buildpack 2. It's available for a limited timeframe \(4 to 6 weeks\).

-   *sap\_java\_buildpack\_jakarta\_<version\_previous\>* – This version used to be latest in the previous update of the SAP BTP, Cloud Foundry environment. It's available for a limited timeframe \(4 to 6 weeks\).

-   *sap\_java\_buildpack\_jakarta\_<version\_before\_previous\>* – This version used to be latest before two updates of the SAP BTP, Cloud Foundry environment. It's available for a limited timeframe \(4 to 6 weeks\).


To check these versions, proceed as follows:

1.  Log in to a particular SAP BTP region and subaccount. For example, if your region is **eu10**, run:

    ```
    cf login -a https://api.cf.eu10.hana.ondemand.com
    ```

2.  Then run:

    ```
    cf buildpacks
    ```




### How to use versions of SAP Java Buildpack 2?

-   **Option 1:** Use the default one – *sap\_java\_buildpack\_jakarta* 

    You take advantage of all latest features and fixes in SAP Java Buildpack 2. This way, it's guaranteed that the buildpack is always available. The drawback in this case is the limited time for adoption, if it's needed. In such a scenario, applications can fall back to an older version temporarily to avoid any downtime.

-   **Option 2:** Set a particular version – *sap\_java\_buildpack\_jakarta\_<version\_suffix\>*

    Bear in mind that this version will only exist for a limited amount of time. This may lead to the situation where application restage is failing because the used version of the buildpack is no longer available. To avoid this, we recommend that you follow the updates of the buildpack and test your applications with its latest version. Developers should never allow their applications to run on an outdated buildpack version.


**Example:**

Let's say that the latest version of SAP Java Buildpack 2 is **2.24.0**. Then, the output of the `cf buildpacks` command would be:

```

buildpack                        position    enabled     locked    filename

sap_java_buildpack_jakarta           1         true      false     sap_java_buildpack_jakarta-v2.23.0.zip
sap_java_buildpack_jakarta_2_23      2         true      false     sap_java_buildpack_jakarta-v2.23.0.zip
sap_java_buildpack_jakarta_2_22      3         true      false     sap_java_buildpack_jakarta-v2.22.0.zip
sap_java_buildpack_jakarta_2_21      4         true      false     sap_java_buildpack_jakarta-v2.21.0.zip
```

When SAP Java Buildpack 2 is updated on the SAP BTP, Cloud Foundry environment from version **2.23.0** to **2.24.0**, the list will change to:

```

buildpack                        position    enabled     locked    filename

sap_java_buildpack_jakarta           1         true      false     sap_java_buildpack_jakarta-v2.24.0.zip
sap_java_buildpack_jakarta_2_24      2         true      false     sap_java_buildpack_jakarta-v2.24.0.zip
sap_java_buildpack_jakarta_2_23      3         true      false     sap_java_buildpack_jakarta-v2.23.0.zip
sap_java_buildpack_jakarta_2_22      4         true      false     sap_java_buildpack_jakarta-v2.22.0.zip
```

This means that *sap\_java\_buildpack\_jakarta\_2\_21* will no longer be available for applications.

> ### Note:  
> No fixes will be provided to older versions of the buildpack. Fixes, including security ones, will be part of the latest version.



### How to switch to a specific buildpack version?

To use *sap\_java\_buildpack\_jakarta\_<version\_suffix\>*, specify its name when pushing an application to the SAP BTP, Cloud Foundry environment:

```
cf push -f <PATH_TO_APP_MANIFEST> -b sap_java_buildpack_jakarta_<version_suffix>
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
  - sap_java_buildpack_jakarta_2_18
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
      buildpack: sap_java_buildpack_jakarta_2_18
...
```



<a name="loio1cf206b5ef7043b282ba87380fcfbfc1__section_dvg_kcz_vtb"/>

## Supported Java Versions

SAP Java Buildpack 2 \(`sap_java_buildpack_jakarta`\) supports the following Java versions:

-   Java **17** – default version. You can obtain it by using SapMachine 17 \(*it provides a JRE with Java 17*\)
-   Java **21** – you can obtain it by using SapMachine 21 \(*it provides a JRE with Java 21*\)

To learn how to configure your application to use SapMachine JRE and JDK, see: [SapMachine](sapmachine-785d6b3.md)



<a name="loio1cf206b5ef7043b282ba87380fcfbfc1__section_yxx_4w3_t2b"/>

## Components

SAP Java Buildpack 2 provides the following components in the application container \(`<APP_ROOT_DIR>/app/META-INF/.sap_java_buildpack_jakarta`\):

-   Runtimes – [Tomcat 10](tomcat-10-97d0e34.md), [TomEE 10](tomee-10-66e808e.md), and [Java Main](java-main-8a1786a.md)

-   [SapMachine](sapmachine-785d6b3.md)

-   [Memory Calculator V2](memory-calculator-v2-8eef959.md)

-   [SAP BTP Security Services Integration Libraries](https://github.com/SAP/cloud-security-services-integration-library) – version 3.x


To check all the components regularly updated in the SAP Java Buildpack 2.x releases, see: [SAP Java Buildpack BOM](https://mvnrepository.com/artifact/com.sap.cloud.sjb.cf/sap-java-buildpack-bom)



<a name="loio1cf206b5ef7043b282ba87380fcfbfc1__section_wg4_djf_krb"/>

## What's New

To see the latest news and updates about SAP Java Buildpack 2, regularly check the release notes on the [What's New portal](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?locale=en-US&Component=SAP%20Java%20Buildpack).



<a name="loio1cf206b5ef7043b282ba87380fcfbfc1__section_cc2_qzf_hvb"/>

## Troubleshooting

If you encounter an issue while using SAP Java Buildpack 2, you can:

-   Search for your problem in our [Troubleshooting](sap-java-buildpack-ee609aa.md) section.

-   Create an incident for your specific problem, using support component **BC-CP-CF-BLDP**. To provide the necessary details, use the following template: [Initial Problem-Related Data](troubleshooting-buildpacks-073b7fc.md) 


