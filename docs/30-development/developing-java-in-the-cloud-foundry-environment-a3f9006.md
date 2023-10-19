<!-- loioa3f90069d6cd41da82f34a6123d82ce6 -->

# Developing Java in the Cloud Foundry Environment

Find selected information for Java development on SAP BTP, Cloud Foundry and references to more detailed sources.

> ### Note:  
> The entire Java section in the navigation tree is dedicated to **SAP Java Buildpack**.
> 
> However, at the bottom of this page, you will also find an extra section about the community [Cloud Foundry Java Buildpack](https://github.com/cloudfoundry/java-buildpack).

SAP Java Buildpack is a Cloud Foundry buildpack for running JVM-based applications. The buildpack provides the following runtimes: [Tomcat](tomcat-ddfc101.md), [TomEE \(Deprecated\)](tomee-deprecated-a9590c2.md), [TomEE 7](tomee-7-79c039a.md), and [Java Main](java-main-8a1786a.md).



<a name="loioa3f90069d6cd41da82f34a6123d82ce6__section_xxx_4w3_t2b"/>

## Usage

To use this buildpack, specify its name when pushing an application to SAP BTP, Cloud Foundry:

```
cf push -f <PATH_TO_APP_MANIFEST> -b sap_java_buildpack
```

You can also use the buildpack attribute to specify it in the `manifest.yml` file:

```
---
applications:
- name: <APP_NAME>
  buildpacks:
  - sap_java_buildpack
  ...
```

or in the `mtad.yml` file of your archive:

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



<a name="loioa3f90069d6cd41da82f34a6123d82ce6__section_czc_1hd_kgb"/>

## Buildpack Versioning

The SAP BTP, Cloud Foundry environment provides four versions of SAP Java Buildpack as part of its system buildpacks:

-   *sap\_java\_buildpack* - Holds the latest available version of SAP Java Buildpack. All new features and fixes are provided with this version.

-   *sap\_java\_buildpack\_<version\_latest\>* - Holds the latest available version of SAP Java Buildpack; available for a limited timeframe \(4 to 6 weeks\).

-   *sap\_java\_buildpack\_<version\_previous\>* - This version used to be latest in the previous update of the SAP BTP, Cloud Foundry environment; available for a limited timeframe \(4 to 6 weeks\).

-   *sap\_java\_buildpack\_<version\_before\_previous\>* - This version used to be latest before two updates of the SAP BTP, Cloud Foundry; available for a limited timeframe \(4 to 6 weeks\).


To check these versions:

1.  Log in to a particular SAP BTP region and subaccount. Run: **`cf api <SAP BTP region>`**

    For example: **`cf api https://api.cf.eu10.hana.ondemand.com`**

2.  Then run: **`cf buildpacks`**




### Considerations about the usage of different versions of SAP Java Buildpack

-   If you always use **sap\_java\_buildpack** – This is the way to go in order to take advantage of any new features and fixes in SAP Java Buildpack. Thus it's guaranteed that the buildpack is always available. The drawback in this case is the limited time for any adoption which might be needed. In such a scenario, applications can fall back to an older version temporarily to avoid any down time.

-   If you pin a version of the buildpack - developers should be aware of the fact that this version will exist for a limited amount of time. This may lead to the situation where application restage is failing because the used version of the buildpack is not available anymore. To avoid this, it is recommended to follow the updates of the buildpack and test the application with the newest buildpack so that it could be adopted in time \(in case adoption is required\), and to update the version regularly. In this scenario, developers should never allow their application to run on an outdated buildpack version.


**Example:**

Let's say that the latest version of SAP Java Buildpack is **1.50.0**. Then, the output of the `cf buildpacks` command would be:

```
buildpack           position   enabled   locked   filename

sap_java_buildpack           1         true      false    sap_java_buildpack-1.50.0.zip
sap_java_buildpack_1_50      2         true      false    sap_java_buildpack-1.50.0.zip
sap_java_buildpack_1_49      3         true      false    sap_java_buildpack-1.49.0.zip
sap_java_buildpack_1_48      4         true      false    sap_java_buildpack-1.48.0.zip
```

When SAP Java Buildpack is updated on the SAP BTP, Cloud Foundry from version **1.50.0** to **1.51.0**, the list will change to:

```
buildpack           position   enabled   locked   filename

sap_java_buildpack           1         true      false    sap_java_buildpack-1.51.0.zip
sap_java_buildpack_1_51      2         true      false    sap_java_buildpack-1.51.0.zip
sap_java_buildpack_1_50      3         true      false    sap_java_buildpack-1.50.0.zip
sap_java_buildpack_1_49      4         true      false    sap_java_buildpack-1.49.0.zip
```

This means that *sap\_java\_buildpack\_1\_48* will no longer be available for applications.

> ### Note:  
> No fixes will be provided to the older versions of the buildpack. Fixes, including security ones, will be part of the latest version.



### Switching to a different version of the buildpack

To use *sap\_java\_buildpack\_<version\_suffix\>*, specify its name when pushing an application to SAP BTP, Cloud Foundry:

```
cf push -f <PATH_TO_APP_MANIFEST> -b sap_java_buildpack_<version_suffix>
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
  - sap_java_buildpack
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
      buildpack: sap_java_buildpack_1_50
...
```



<a name="loioa3f90069d6cd41da82f34a6123d82ce6__section_dvg_kcz_vtb"/>

## Supported Versions

The SAP Java Buildpack \(`sap_java_buildpack`\) supports the following Java versions:

-   Java **8** – default version when you use SAP JVM \(*it provides a JRE with Java 8*\)
-   Java **11** – default version when you use SapMachine \(*it provides a JRE with Java 11*\)
-   Java **17** – possible version when you use SapMachine \(*it provides a JRE with Java 17*\)

To learn how to configure your application to use SapMachine JRE and JDK, see: [SapMachine](sapmachine-785d6b3.md)



<a name="loioa3f90069d6cd41da82f34a6123d82ce6__section_yxx_4w3_t2b"/>

## Components

SAP Java Buildpack provides the following components \(containers, JREs, frameworks\) in the application container \(`<APP_ROOT_DIR>/app/META-INF/.sap_java_buildpack`\):

-   Runtime – [Tomcat](tomcat-ddfc101.md), [TomEE \(Deprecated\)](tomee-deprecated-a9590c2.md), [TomEE 7](tomee-7-79c039a.md), and [Java Main](java-main-8a1786a.md)

-   [Memory Calculator V1 \(SAP JVM Memory Calculator\)](memory-calculator-v1-sap-jvm-memory-calculator-c1059e0.md) - optional

-   [Memory Calculator V2](memory-calculator-v2-8eef959.md) - default

-   SAP JVM

-   Log Level Client

-   JVMKill Agent




<a name="loioa3f90069d6cd41da82f34a6123d82ce6__section_m1p_3w4_jyb"/>

## Async Servlets

In the current version of the SAP Java Buildpack, the async servlets are *not supported*.

**Reason:** Some of the [valves](https://tomcat.apache.org/tomcat-8.0-doc/config/valve.html) that SAP Java Buildpack brings to Tomcat and TomEE 7 are not "async enabled".



<a name="loioa3f90069d6cd41da82f34a6123d82ce6__section_wg4_djf_krb"/>

## What's New

To see the latest news and updates about SAP Java Buildpack, regularly check the release notes on the [What's New portal](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?locale=en-US&Component=SAP%20Java%20Buildpack).



<a name="loioa3f90069d6cd41da82f34a6123d82ce6__section_cc2_qzf_hvb"/>

## Troubleshooting

If you encounter an issue while using SAP Java Buildpack, you can:

-   Search for your problem in our Guided Answers: [SAP Java Buildpack](https://ga.support.sap.com/dtp/viewer/#/tree/3254/actions/51226:51219/?version=current)

-   Create an incident for your specific problem, using support component **BC-CP-CF-BLDP**. To provide the necessary details, use the following template: [Initial Problem-Related Data](https://ga.support.sap.com/dtp/viewer/#/tree/3254/actions/51226:51220/?version=current) 


See also:

-   SAP Note: [3261748](https://me.sap.com/notes/3261748) *SapMachine is replacing OpenJDK 11 & 17 in java\_buildpack*
-   SAP Note: [3214025](https://me.sap.com/notes/3214025) *Migrating Java Applications from TomEE 1.7 to TomEE 7*
-   SAP Note: [3155402](https://me.sap.com/notes/3155402) *Explicitly pin SAP Java Buildpack 1.48.1 in your manifest file*



<a name="loioa3f90069d6cd41da82f34a6123d82ce6__section_ugc_sbl_15b"/>

## Java Tutorial

The following tutorial will guide you through creating a Java application in Cloud Foundry Command Line Interface \(cf CLI\), consuming Cloud Foundry services, and setting up authentication and authorization checks. See: [Create an Application with SAP Java Buildpack](https://developers.sap.com/tutorials/btp-cf-buildpacks-java-create.html)



<a name="loioa3f90069d6cd41da82f34a6123d82ce6__section_urd_l5c_nvb"/>

## Community Cloud Foundry Java Buildpack

This section lists Cloud Foundry Java components and updates maintained by SAP that belong to the online community [Java Buildpack](https://github.com/cloudfoundry/java-buildpack).

-   **SapMachine** – as of [v4.55](https://github.com/cloudfoundry/java-buildpack/releases/tag/v4.55) of the Java Buildpack, SAP has provides SapMachine 11 and 17 instead of OpenJDK 11 and 17 in the offline **`java_buildpack`**. For more information, see SAP Note: [3261748](https://me.sap.com/notes/3261748) *SapMachine is replacing OpenJDK 11 & 17 in java\_buildpack*


