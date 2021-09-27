<!-- loioa3f90069d6cd41da82f34a6123d82ce6 -->

# Developing Java in the Cloud Foundry Environment

Find selected information for Java development on SAP BTP, Cloud Foundry and references to more detailed sources.

The SAP Java buildpack is a Cloud Foundry buildpack for running JVM-based applications. The buildpack provides the following runtimes: [Tomcat](Application_Containers_83d2416.md#loioddfc10180fe844049cc71f6989942dc2), [TomEE](Application_Containers_83d2416.md#loioa9590c2f5ebc4d1586d9f0f53a60cfdc), [TomEE 7](Application_Containers_83d2416.md#loio79c039ab43b946a7b50c5d0326a3b40b), and [Java Main](Application_Containers_83d2416.md#loio8a1786acd70445768b35e50f3038a2a9).



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

or in the `mtad.yml` of your mtar archive:

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

-   Runtime \([Tomcat](Application_Containers_83d2416.md#loioddfc10180fe844049cc71f6989942dc2), [TomEE](Application_Containers_83d2416.md#loioa9590c2f5ebc4d1586d9f0f53a60cfdc), [TomEE 7](Application_Containers_83d2416.md#loio79c039ab43b946a7b50c5d0326a3b40b), [Java Main](Application_Containers_83d2416.md#loio8a1786acd70445768b35e50f3038a2a9)\)

-   [Memory Calculator V1 \(SAP JVM Memory Calculator\)](Memory_Calculator_505a71a.md#loioc1059e056aad406297addcd177a4fb7c) - by default

-   [Memory Calculator V2](Memory_Calculator_505a71a.md#loio8eef9590a1d24e87af239d7c7e15fffe) - optional

-   SAP JVM

-   Log Level Client

-   JVMKill Agent


-   **[Application Containers](Application_Containers_83d2416.md#loio83d241613dcd41c99ccc308ed0d26399 "The following application containers are available for usage with the SAP Java
		Buildpack.")**  
The following application containers are available for usage with the SAP Java Buildpack.
-   **[Customizing the Java Virtual Machine \(JVM\) Settings](Customizing_the_Java_Virtual_Machine_(JVM)_Settings_b8cda61.md#loiob8cda61d3d984e259f1de8816e52ec47 "")**  

-   **[Overriding Resources in Droplet](Overriding_Resources_in_Droplet_0a34588.md "Applications can override resources in the droplet by placing files in
			META-INF/sap_java_buildpack/resources/. These files override files
		inside the droplet that have the same relative path to the droplet root.")**  
Applications can override resources in the droplet by placing files in `META-INF/sap_java_buildpack/resources/`. These files override files inside the droplet that have the same relative path to the droplet root.
-   **[Resource Configuration](Resource_Configuration_c893e9c.md)**  

-   **[Context Root Redirect](Context_Root_Redirect_582d405.md "The SAP Java Buildpack provides context root redirect functionality. ")**  
The SAP Java Buildpack provides context root redirect functionality.
-   **[Logging and Tracing](Logging_and_Tracing_7eb922a.md)**  

-   **[Debugging Java Applications](Debugging_Java_Applications_1e7376f.md#loio1e7376fa1a8a4cefbed5c87693af4e6a "You can debug an application running on a Cloud                                 Foundry 		container that is using SAP JVM. By using SAP JVM, you can enable debugging on-demand 		without having to restart the application or the JVM.Debug an application running on a Cloud Foundry container that is using 		SAPMachine.You can debug an application running on a Cloud                                 Foundry 		container that is using the standard Java community build pack.")**  
You can debug an application running on a Cloud Foundry container that is using SAP JVM. By using SAP JVM, you can enable debugging on-demand without having to restart the application or the JVM.Debug an application running on a Cloud Foundry container that is using SAPMachine.You can debug an application running on a Cloud Foundry container that is using the standard Java community build pack.
-   **[Dynatrace Integration](Dynatrace_Integration_1610eac.md)**  

-   **[Multiple Buildpack Framework](Multiple_Buildpack_Framework_b2662e8.md "The Multiple Buildpack Framework enables the SAP Java Buildpack to act as the final
		buildpack in a multiple buildpack deployment. It reads the contributions of other, earlier
		buildpacks and incorporates them into its standard staging.")**  
The Multiple Buildpack Framework enables the SAP Java Buildpack to act as the final buildpack in a multiple buildpack deployment. It reads the contributions of other, earlier buildpacks and incorporates them into its standard staging.
-   **[Configuring a Database Connection](Configuring_a_Database_Connection_7568c3d.md#loio7568c3d036f34a64bb6595b55805bffb "Define details of the database connection used by your Java Web Application running on 		Cloud Foundry Environment with the SAP Java Buildpack.")**  
Define details of the database connection used by your Java Web Application running on Cloud Foundry Environment with the SAP Java Buildpack.
-   **[SAP Java Connector](SAP_Java_Connector_3cee866.md "The SAP Java buildpack provides an option to use the SAP Java Connector.")**  
The SAP Java buildpack provides an option to use the SAP Java Connector.
-   **[Profiling an Application Running on SAP JVM](Profiling_an_Application_Running_on_SAP_JVM_e709773.md "The SAP JVM Profiler is a tool that helps you analyze the resource consumption of a Java
		application running on SAP Java Virtual Machine (JVM). You can use it to profile simple
		stand-alone Java programs or complex enterprise applications.")**  
The SAP JVM Profiler is a tool that helps you analyze the resource consumption of a Java application running on SAP Java Virtual Machine \(JVM\). You can use it to profile simple stand-alone Java programs or complex enterprise applications.
-   **[Bill of Materials \(BOM\)](Bill_of_Materials_(BOM)_6c6936e.md " For Maven projects, the versions of the SAP Java Buildpack dependencies and the APIs provided by supported runtime containers can be
        consumed through a Bill Of Materials (BOM).")**  
 For Maven projects, the versions of the SAP Java Buildpack dependencies and the APIs provided by supported runtime containers can be consumed through a Bill Of Materials \(BOM\).

