<!-- loio785d6b390b834bee818e242160f87df5 -->

# SapMachine

SapMachine provides a Java Runtime Environment \(JRE\) with Java 11, 17, 21, and 25.



SapMachine works with the following application containers:

-   [TomEE 7](tomee-7-79c039a.md)

-   [TomEE 10](tomee-10-66e808e.md)

-   [Tomcat 9](tomcat-9-ddfc101.md)

-   [Tomcat 10](tomcat-10-97d0e34.md)

-   [Java Main](java-main-8a1786a.md)


> ### Caution:  
> **Only relevant to SAP Java Buildpack 1:** 
> 
> -   SAP Java Buildpack 1 has been deprecated and is going to be **removed** from SAP BTP, Cloud Foundry environment on **December 31, 2025**. See: [SAP Java Buildpack 1 – DEPRECATED!](sap-java-buildpack-1-deprecated-ad3e8df.md)
> 
> -   TomEE 7 supports only Java 7 and 8. Thus, even if your TomEE 7 application runs successfully with SapMachine JRE 17, at some point it might crash. Also, TomEE 7 has already reached [end of life](https://tomee.apache.org/tomee-7.1-eol.html). See: [Discontinued TomEE versions](https://tomee.apache.org/download-discontinued.html)



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

Without specifying a particular JRE version, your application will use the following default offline JRE, bundled within the buildpack:

-   For SAP Java Buildpack 1 – SapMachine JRE 11 \(deprecated!\)

-   For SAP Java Buildpack 2 – SapMachine JRE 17


To specify a particular JRE version, use environment variable JBP\_CONFIG\_SAP\_MACHINE\_JRE.

By default, the `use_offline_repository` parameter is set to *true*. That means, your application will use the offline SapMachine JRE provided by the buildpack.

If you set this parameter to *false*, the buildpack will attempt to download SapMachine JRE of a particular version from the GitHub asset repository. This will only work if your Cloud Foundry instance has access to [GitHub: SapMachine](https://github.com/SAP/SapMachine).



### SapMachine 11 \(deprecated!\)

We recommend that you use the latest stable version, which is available in the major version of SapMachine JRE 11. Set the JBP\_CONFIG\_SAP\_MACHINE\_JRE variable like this:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
    JBP_CONFIG_SAP_MACHINE_JRE: '{ version: 11.+ }'
```

In some cases, it can be helpful to pin a particular published version of SapMachine JRE 11. To make the buildpack download this JRE version \(for example, 11.0.28\), specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
    JBP_CONFIG_SAP_MACHINE_JRE: '{use_offline_repository: false, version: 11.0.28 }'
  ...
```

**NOTE:** To stay secure, you need to update this version string on your own. For this reason, SAP does **not** recommend this approach.



### SapMachine 17

> ### Tip:  
> SAP Java Buildpack 1 and 2 provide a customized SapMachine JRE 17 that contains a [jdk.compiler](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.compiler/module-summary.html) module.

We recommend that you use the latest stable version, which is available in the major version of SapMachine JRE 17. Set the JBP\_CONFIG\_SAP\_MACHINE\_JRE variable like this:

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

We recommend that you use the latest stable version, which is available in the major version of SapMachine JRE 21. Set the JBP\_CONFIG\_SAP\_MACHINE\_JRE variable like this:

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

We recommend that you use the latest stable version, which is available in the major version of SapMachine JRE 25. Set the JBP\_CONFIG\_SAP\_MACHINE\_JRE variable like this:

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
> SapMachine JDK is **not bundled** within the buildpack. Therefore, if you want to use SapMachine JDK 11 \(deprecated\) or SapMachine JDK 17, 21 or 25, you have to download it from the [GitHub project](https://sapmachine.io/) as an online component.
> 
> However, you can use the [jdk.compiler](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.compiler/module-summary.html) module, which is **provided** by the buildpack as part of the customized SapMachine JRE, v. 17, 21 and 25. To learn more, see section [Activation Using JRE](sapmachine-785d6b3.md#loio785d6b390b834bee818e242160f87df5__section_jre).

To specify an online JDK version \(17, 21, or 25\), use environment variable JBP\_CONFIG\_SAP\_MACHINE\_JDK.



### SapMachine 11 \(deprecated!\)

We recommend that you use the latest stable version, which is available in the major version of SapMachine JDK 11. Set the JBP\_CONFIG\_SAP\_MACHINE\_JDK variable like this:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: '{ version: 11.+ }'
```

In some cases, it can be helpful to pin a particular published version of SapMachine JDK 11. To make the buildpack download this JDK version \(for example, 11.0.28\), specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: '{ version: 11.0.28 }'
  ...
```

**NOTE:** To stay secure, you need to update this version string on your own. For this reason, SAP does **not** recommend this approach.



### SapMachine 17

We recommend that you use the latest stable version, which is available in the major version of SapMachine JDK 17. Set the JBP\_CONFIG\_SAP\_MACHINE\_JDK variable like this:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: '{ version: 17.+ }'
```

In some cases, it can be helpful to pin a particular published version of SapMachine JDK 17. To make the buildpack download this JDK version \(for example, 17.0.17\), specify it the following way:

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

We recommend that you use the latest stable version, which is available in the major version of SapMachine JDK 21. Set the JBP\_CONFIG\_SAP\_MACHINE\_JDK variable like this:

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

We recommend that you use the latest stable version, which is available in the major version of SapMachine JDK 25. Set the JBP\_CONFIG\_SAP\_MACHINE\_JDK variable like this:

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


[https://sapmachine.io/](https://sapmachine.io/)

[SAP Java Buildpack 2](sap-java-buildpack-2-1cf206b.md "SAP Java Buildpack 2 is a Cloud Foundry buildpack for running SapMachine-based applications.")

[Runtimes and Containers](runtimes-and-containers-83d2416.md "Find out which application runtimes and containers you can use, depending on the Java buildpack your application is using.")

[Debug an Application Running on SapMachine](debug-an-application-running-on-sapmachine-f7fa9f3.md "Debug a Java web application running on a Cloud Foundry container that uses SapMachine.")

[Configure a Java Application for Logs and Traces](configure-a-java-application-for-logs-and-traces-5551c5e.md "Configure the collection of log and trace messages generated by a Java application in SAP BTP, Cloud Foundry.")

