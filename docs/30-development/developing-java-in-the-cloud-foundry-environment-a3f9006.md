<!-- loioa3f90069d6cd41da82f34a6123d82ce6 -->

# Developing Java in the Cloud Foundry Environment

Find selected information for Java development on SAP BTP, Cloud Foundry and references to more detailed sources.

The SAP Java buildpack is a Cloud Foundry buildpack for running JVM-based applications. The buildpack provides the following runtimes: [Tomcat](application-containers-83d2416.md#loioddfc10180fe844049cc71f6989942dc2), [TomEE](application-containers-83d2416.md#loioa9590c2f5ebc4d1586d9f0f53a60cfdc), [TomEE 7](application-containers-83d2416.md#loio79c039ab43b946a7b50c5d0326a3b40b), and [Java Main](application-containers-83d2416.md#loio8a1786acd70445768b35e50f3038a2a9).



<a name="loioa3f90069d6cd41da82f34a6123d82ce6__section_xxx_4w3_t2b"/>

## Usage

To use this buildpack specify its name when pushing an application to Cloud Foundry.

```
cf push -f <PATH_TO_APP_MANIFEST> -b sap_java_buildpack
```

You can also use the buildpack attribute to specify it in the `manifest.yml` file:

```
---
applications:
- name: <APP_NAME>
  buildpacks: sap_java_buildpack
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

## Versioning

The SAP BTP, Cloud Foundry environment provides four versions of the SAP Java Buildpack as part of its system buildpacks:

-   *sap\_java\_buildpack* - Always holds the latest available version of the SAP Java Buildpack. All new features and fixes are provided with this version.

-   *sap\_java\_buildpack\_<version\_latest\>* - Holds the latest available version of the SAP Java Buildpack; available for a limited timeframe \(four to six weeks\).

-   *sap\_java\_buildpack\_<version\_previous\>* - This version used to be latest in the previous update of the Cloud Foundry environment; available for a limited timeframe \(four to six weeks\).

-   *sap\_java\_buildpack\_<version\_before\_previous\>* - This version used to be latest before two updates of the Cloud Foundry environment; available for a limited timeframe \(four to six weeks\).




### Important considerations about the usage of the different versions of SAP Java Buildpack

-   If you always use *sap\_java\_buildpack* - This is the way to go in order to take advantage of any new features and fixes in the SAP Java buildpack. Thus it is guaranteed that the buildpack is always available. The drawback in this case is the limited time for any adoption which might be needed. In such a scenario applications can fall back to an older version temporarily to avoid any down time.

-   If you pin the version of the buildpack - developers should be aware of the fact that this version will exist for a limited amount of time. This may lead to the situation where a restage is failing because the used version of the buildpack is not available anymore. To avoid this, it is recommended to follow the updates of the buildpack and test the application with the newest buildpack so that it could be adopted in time, in case an adoption is required, and to update the version regularly. In this scenario developers should never allow their applciaiton to run on an outdated buildpack version.


For clarity below is an example how the version update will takes place:

Provided that the latest version of the SAP Java Buildpack is 1.2.3, the output of the cf buildpacks command would be:

```
	buildpack           position   enabled   locked   filename

sap_java_buildpack            a         true      false    sap_java_buildpack-1.2.3.zip
sap_java_buildpack_1_2_3      b         true      false    sap_java_buildpack-1.2.3.zip
sap_java_buildpack_1_2_2      c         true      false    sap_java_buildpack-1.2.2.zip
sap_java_buildpack_1_2_1      d         true      false    sap_java_buildpack-1.2.1.zip
```

When the SAP Java buildpack is updated on the Cloud Foundry environment from v.1.2.3 to v.1.2.4 the list will change to:

```
	buildpack           position   enabled   locked   filename

sap_java_buildpack            a         true      false    sap_java_buildpack-1.2.4.zip
sap_java_buildpack_1_2_4      b         true      false    sap_java_buildpack-1.2.4.zip
sap_java_buildpack_1_2_3      c         true      false    sap_java_buildpack-1.2.3.zip
sap_java_buildpack_1_2_2      d         true      false    sap_java_buildpack-1.2.2.zip
```

making sap\_java\_buildpack\_1\_2\_1 no longer available for applications.

> ### Note:  
> No fixes will be provided to the older versions of the buildpack. Fixes, including security fixes, will be part of the latest version.



### Switching to different version of Buildpack

To use *sap\_java\_buildpack\_<version\_suffix\>* version of the buildpack, specify its name when pushing an application to Cloud Foundry:

 `cf push -f <PATH_TO_APP_MANIFEST> -b sap_java_buildpack_<version_suffix>` 

or use the buildpack attribute to specify it in the `manifest.yml`:

```
---
applications:
- name: application-name
  memory: 128M
  path: ./target/application-name.war
  instances: 1
  buildpacks: sap_java_buildpack_<version_suffix>
```

or in the `mtad.yml` of your **mtar** archive:

```
...
modules:
  - name: application-name
    type: java.tomcat
    path: ./target/application-name.war
    properties:
      ...
    parameters:
      ...
      memory: 512M
      buildpack: sap_java_buildpack_<version_suffix>
...
```



<a name="loioa3f90069d6cd41da82f34a6123d82ce6__section_yxx_4w3_t2b"/>

## Components

The SAP Java buildpack provides the following components \(containers, jres, frameworks\) in the application container \(`<APP_ROOT_DIR>/app/META-INF/.sap_java_buildpack`\):

-   Runtime \([Tomcat](application-containers-83d2416.md#loioddfc10180fe844049cc71f6989942dc2), [TomEE](application-containers-83d2416.md#loioa9590c2f5ebc4d1586d9f0f53a60cfdc), [TomEE 7](application-containers-83d2416.md#loio79c039ab43b946a7b50c5d0326a3b40b), [Java Main](application-containers-83d2416.md#loio8a1786acd70445768b35e50f3038a2a9)\)

-   [Memory Calculator V1 \(SAP JVM Memory Calculator\)](memory-calculator-505a71a.md#loioc1059e056aad406297addcd177a4fb7c) - optional

-   [Memory Calculator V2](memory-calculator-505a71a.md#loio8eef9590a1d24e87af239d7c7e15fffe) - default

-   SAP JVM

-   Log Level Client

-   JVMKill Agent




<a name="loioa3f90069d6cd41da82f34a6123d82ce6__section_wg4_djf_krb"/>

## Release Notes

To see the latest news and updates about the SAP Java Buildpack, regularly check the release notes on the [What's New portal](https://help.sap.com/doc/43b304f99a8145809c78f292bfc0bc58/Cloud/en-US/98bf747111574187a7c76f8ced51cfeb.html?sel1=SAP%20Java%20Buildpack&from=2021-01-01).

