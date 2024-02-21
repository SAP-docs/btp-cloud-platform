<!-- loioad3e8dfdbaad423e96ca875a4cd36f61 -->

# SAP Java Buildpack

SAP Java Buildpack is a Cloud Foundry buildpack for running JVM-based applications.

The buildpack supports the following runtimes:

-   [TomEE 7](tomee-7-79c039a.md)

-   [Tomcat 9](tomcat-9-ddfc101.md)

-   [Java Main](java-main-8a1786a.md)




<a name="loioad3e8dfdbaad423e96ca875a4cd36f61__section_xxx_4w3_t2b"/>

## Usage

To use this buildpack, specify its name when deploying a Java application to SAP BTP, Cloud Foundry:

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



<a name="loioad3e8dfdbaad423e96ca875a4cd36f61__section_czc_1hd_kgb"/>

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




### How to use the SAP Java Buildpack versions?

-   Use the default **sap\_java\_buildpack**

-   Set a particular version of the buildpack - Bear in mind that this version will exist for a limited amount of time. This may lead to the situation where application restage is failing because the used version of the buildpack is no longer available. To avoid this, we recommend that you follow the updates of the buildpack and test your applications with the latest buildpack version. Developers should never allow their applications to run on an outdated buildpack version. – You take advantage of all latest features and fixes in SAP Java Buildpack. This way, it's guaranteed that the buildpack is always available. The drawback in this case is the limited time for any adoption which might be needed. In such a scenario, applications can fall back to an older version temporarily to avoid any downtime.


**Example:**

Let's say that the latest version of SAP Java Buildpack is **1.80.0**. Then, the output of the `cf buildpacks` command would be:

```
buildpack           position   enabled   locked   filename

sap_java_buildpack           1         true      false    sap_java_buildpack-1.80.0.zip
sap_java_buildpack_1_80      2         true      false    sap_java_buildpack-1.80.0.zip
sap_java_buildpack_1_79      3         true      false    sap_java_buildpack-1.79.0.zip
sap_java_buildpack_1_78      4         true      false    sap_java_buildpack-1.78.0.zip
```

When SAP Java Buildpack is updated on the SAP BTP, Cloud Foundry from version **1.80.0** to **1.81.0**, the list will change to:

```
 – You take advantage of all latest features and fixes in SAP Javabuildpack           position   enabled   locked   filename

sap_java_buildpack           1         true      false    sap_java_buildpack-1.81.0.zip
sap_java_buildpack_1_81      2         true      false    sap_java_buildpack-1.81.0.zip
sap_java_buildpack_1_80      3         true      false    sap_java_buildpack-1.80.0.zip
sap_java_buildpack_1_79      4         true      false    sap_java_buildpack-1.79.0.zip
```

This means that *sap\_java\_buildpack\_1\_78* will no longer be available for applications.

> ### Note:  
> No fixes will be provided to older versions of the buildpack. Fixes, including security ones, will be part of the latest version.



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
  - sap_java_buildpack_1_80
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
      buildpack: sap_java_buildpack_1_80
...
```



<a name="loioad3e8dfdbaad423e96ca875a4cd36f61__section_dvg_kcz_vtb"/>

## Supported Versions

The SAP Java Buildpack \(`sap_java_buildpack`\) supports the following Java versions:

-   Java **8** – default version when you use SAP JVM \(*it provides JRE and JDK with Java 8*\)
-   Java **11** – default version when you use SapMachine \(*it provides JRE and JDK with Java 11*\)
-   Java **17** – possible version when you use SapMachine \(*it provides JRE and JDK with Java 17*\)

To learn how to configure your application to use SapMachine JRE and JDK, see: [SapMachine](sapmachine-785d6b3.md)



<a name="loioad3e8dfdbaad423e96ca875a4cd36f61__section_yxx_4w3_t2b"/>

## Components

SAP Java Buildpack provides the following components \(containers, JREs, frameworks\) in the application container \(`<APP_ROOT_DIR>/app/META-INF/.sap_java_buildpack`\):

-   Runtime – [Tomcat 9](tomcat-9-ddfc101.md), [TomEE 7](tomee-7-79c039a.md) and [Java Main](java-main-8a1786a.md)

-   Memory Calculator – [Memory Calculator V2](memory-calculator-v2-8eef959.md) \(default\) and [Memory Calculator V1](memory-calculator-v1-sap-jvm-memory-calculator-c1059e0.md) \(optional\)

-   [SapMachine](sapmachine-785d6b3.md)

-   SAP JVM

-   Log Level Client

-   JVMKill Agent




<a name="loioad3e8dfdbaad423e96ca875a4cd36f61__section_m1p_3w4_jyb"/>

## Async Servlets

In the current version of the SAP Java Buildpack, the async servlets are *not supported*.

**Reason:** Some of the [valves](https://tomcat.apache.org/tomcat-8.0-doc/config/valve.html) that SAP Java Buildpack brings to Tomcat and TomEE 7 are not "async enabled".



<a name="loioad3e8dfdbaad423e96ca875a4cd36f61__section_wg4_djf_krb"/>

## What's New

To see the latest news and updates about SAP Java Buildpack, regularly check the release notes on the [What's New portal](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?locale=en-US&Component=SAP%20Java%20Buildpack).



<a name="loioad3e8dfdbaad423e96ca875a4cd36f61__section_cc2_qzf_hvb"/>

## Troubleshooting

If you encounter an issue while using SAP Java Buildpack, you can:

-   Search for your problem in our Guided Answers: [SAP Java Buildpack](https://ga.support.sap.com/dtp/viewer/#/tree/3254/actions/51226:51219/?version=current)

-   Create an incident for your specific problem, using support component **BC-CP-CF-BLDP**. To provide the necessary details, use the following template: [Initial Problem-Related Data](https://ga.support.sap.com/dtp/viewer/#/tree/3254/actions/51226:51220/?version=current) 


See also:

-   SAP Note: [3261748](https://me.sap.com/notes/3261748) *SapMachine is replacing OpenJDK 11 & 17 in java\_buildpack*
-   SAP Note: [3214025](https://me.sap.com/notes/3214025) *Migrating Java Applications from TomEE 1.7 to TomEE 7*



<a name="loioad3e8dfdbaad423e96ca875a4cd36f61__section_ugc_sbl_15b"/>

## Java Tutorial

The following tutorial will guide you through creating a Java application in Cloud Foundry Command Line Interface \(cf CLI\), consuming Cloud Foundry services, and setting up authentication and authorization checks. See: [Create an Application with SAP Java Buildpack](https://developers.sap.com/tutorials/btp-cf-buildpacks-java-create.html)

