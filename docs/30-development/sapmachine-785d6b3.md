<!-- loio785d6b390b834bee818e242160f87df5 -->

# SapMachine

SapMachine provides a Java Runtime Environment \(JRE\) with Java 17, 21, and 25.



SapMachine works with the following application containers:

-   [TomEE 7](tomee-7-79c039a.md)

-   [TomEE 10](tomee-10-66e808e.md)

-   [Tomcat 9](tomcat-9-ddfc101.md)

-   [Tomcat 10](tomcat-10-97d0e34.md)

-   [Java Main](java-main-8a1786a.md)


<a name="loio785d6b390b834bee818e242160f87df5__section_jre"/>

## Activation Using JRE

To activate SapMachine **JRE** in SAP Java Buildpack, add the following environment variable:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
  ...
```

Without specifying a particular JRE version, your application will currently use the following default offline JRE, bundled within the buildpack:

-   For SAP Java Buildpack 2 – SapMachine JRE 17

NOTE: The default major version of the SapMachine JRE will be raised from 17 to either 21 or 25. This only matters when the major version isn’t explicitly specified.

To specify a particular JRE version, use environment variable JBP\_CONFIG\_SAP\_MACHINE\_JRE.

By default, the `use_offline_repository` parameter is set to *true*. That means, your application will use the offline SapMachine JRE provided by the buildpack.

If you set this parameter to *false*, the buildpack will attempt to download SapMachine JRE of a particular version from the GitHub asset repository. This will only work if your Cloud Foundry instance has access to [GitHub: SapMachine](https://github.com/SAP/SapMachine).



### SapMachine 17

> ### Tip:  
> SAP Java Buildpack 2 provide a customized SapMachine JRE 17 that contains a [jdk.compiler](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.compiler/module-summary.html) module.

To stay secure, use the latest stable version, which is available in the major version of SapMachine JRE 17. Set the JBP\_CONFIG\_SAP\_MACHINE\_JRE variable like this:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
    JBP_CONFIG_SAP_MACHINE_JRE: '{ version: 17.+ }'
```

In some cases, it can be helpful to pin a particular published version of SapMachine JRE 17. To make the buildpack download this JRE version \(for example, 17.0.17\), specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
    JBP_CONFIG_SAP_MACHINE_JRE: '{use_offline_repository: false, version: 17.0.17 }'
  ...
```

**NOTE:** To stay secure, you need to update this version string on your own. For this reason, SAP does **not** recommend this approach.



### SapMachine 21

> ### Tip:  
> SAP Java Buildpack 2 provides a customized SapMachine JRE 21 that contains a [jdk.compiler](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.compiler/module-summary.html) module.

To stay secure, use the latest stable version, which is available in the major version of SapMachine JRE 21. Set the JBP\_CONFIG\_SAP\_MACHINE\_JRE variable like this:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
    JBP_CONFIG_SAP_MACHINE_JRE: '{ version: 21.+ }'
```

In some cases, it can be helpful to pin a particular published version of SapMachine JRE 21. To make the buildpack download this JRE version \(for example, 21.0.9\), specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
    JBP_CONFIG_SAP_MACHINE_JRE: '{use_offline_repository: false, version: 21.0.9 }'
  ...
```

**NOTE:** To stay secure, you need to update this version string on your own. For this reason, SAP does **not** recommend this approach.



### SapMachine 25

> ### Tip:  
> SAP Java Buildpack 2 provides a customized SapMachine JRE 25 that contains a [jdk.compiler](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.compiler/module-summary.html) module.

To stay secure, use the latest stable version, which is available in the major version of SapMachine JRE 25. Set the JBP\_CONFIG\_SAP\_MACHINE\_JRE variable like this:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
    JBP_CONFIG_SAP_MACHINE_JRE: '{ version: 25.+ }'
```

In some cases, it can be helpful to pin a particular published version of SapMachine JRE 25. To make the buildpack download this JRE version \(for example, 25.0.1\), specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
    JBP_CONFIG_SAP_MACHINE_JRE: '{use_offline_repository: false, version: 25.0.1 }'
  ...
```

**NOTE:** To stay secure, you need to update this version string on your own. For this reason, SAP does **not** recommend this approach.



<a name="loio785d6b390b834bee818e242160f87df5__section_jdk"/>

## Activation Using JDK

To use SapMachine **JDK**, add the following environment variable:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
  ...
```

> ### Note:  
> SapMachine JDK is **not bundled** within the buildpack. Therefore, if you want to use SapMachine JDK 17, 21 or 25, you have to download it from the [GitHub project](https://sap.github.io/SapMachine/) as an online component.
> 
> However, you can use the [jdk.compiler](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.compiler/module-summary.html) module, which is **provided** by the buildpack as part of the customized SapMachine JRE, v. 17, 21, and 25. To learn more, see section [Activation Using JRE](sapmachine-785d6b3.md#loio785d6b390b834bee818e242160f87df5__section_jre).

To specify an online JDK version \(17, 21, or 25\), use environment variable JBP\_CONFIG\_SAP\_MACHINE\_JDK.



### SapMachine 17

To stay secure, use the latest stable version, which is available in the major version of SapMachine JDK 17. Set the JBP\_CONFIG\_SAP\_MACHINE\_JDK variable like this:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: '{ version: 17.+ }'
```

In some cases, it can be helpful to pin a particular published version of SapMachine JDK 17. To make the buildpack download this JDK version \(for example, 17.0.16\), specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: '{ version: 17.0.17 }'
  ...
```

**NOTE:** To stay secure, you need to update this version string on your own. For this reason, SAP does **not** recommend this approach.



### SapMachine 21

To stay secure, use the latest stable version, which is available in the major version of SapMachine JDK 21. Set the JBP\_CONFIG\_SAP\_MACHINE\_JDK variable like this:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: '{ version: 21.+ }'
```

In some cases, it can be helpful to pin a particular published version of SapMachine JDK 21. To make the buildpack download this JDK version \(for example, 21.0.9\), specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: '{ version: 21.0.9 }'
  ...
```

**NOTE:** To stay secure, you need to update this version string on your own. For this reason, SAP does **not** recommend this approach.



### SapMachine 25

To stay secure, use the latest stable version, which is available in the major version of SapMachine JDK 25. Set the JBP\_CONFIG\_SAP\_MACHINE\_JDK variable like this:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: '{ version: 25.+ }'
```

In some cases, it can be helpful to pin a particular published version of SapMachine JDK 25. To make the buildpack download this JDK version \(for example, 25.0.1\), specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: '{ version: 25.0.1 }'
  ...
```

**NOTE:** To stay secure, you need to update this version string on your own. For this reason, SAP does **not** recommend this approach.


**Related Information**  

[https://sapmachine.io/](https://sapmachine.io/ "The SapMachine Website with downloads and documentation.")

[Java Main](java-main-8a1786a.md "Find out how you can create a Java application that starts its own runtime. This allows the usage of frameworks and Java runtimes, such as Spring Boot, Jetty, Undertow, or Netty.")

[SAP Java Buildpack 2](sap-java-buildpack-2-1cf206b.md "Find information about SAP Java Buildpack 2 which is a Cloud Foundry buildpack for running SapMachine-based applications.")

[Debug an Application Running on SapMachine](debug-an-application-running-on-sapmachine-f7fa9f3.md "Find out possibilties how to debug a Java web application running on a Cloud Foundry container that uses SapMachine.")

[Runtimes and Containers](runtimes-and-containers-83d2416.md "Find out which application runtimes and containers you can use, depending on the Java buildpack your application is using.")

