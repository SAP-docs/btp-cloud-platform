<!-- loio785d6b390b834bee818e242160f87df5 -->

# SapMachine

SapMachine is an alternative to SAP JVM, and provides a Java Runtime Environment \(JRE\) with Java 11, 17, and 21.



SapMachine works with the following application containers:

-   [TomEE 7](tomee-7-79c039a.md)

-   [Tomcat 9](tomcat-9-ddfc101.md)

-   [Tomcat 10](tomcat-10-97d0e34.md)

-   [Java Main](java-main-8a1786a.md)


> ### Caution:  
> **Only relevant to SAP Java Buildpack 1:** 
> 
> Bear in mind that TomEE 7 supports only Java 7 and 8. Thus, even if your TomEE 7 application runs successfully with SapMachine JRE 17, at some point it might crash. Also, TomEE 7 has already [reached end of life](https://tomee.apache.org/tomee-7.1-eol.html). See: [Discontinued TomEE versions](https://tomee.apache.org/download-discontinued.html)



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

-   For SAP Java Buildpack 1 – SapMachine JRE 11

-   For SAP Java Buildpack 2 – SapMachine JRE 17


To specify a particular JRE version, use environment variable JBP\_CONFIG\_SAP\_MACHINE\_JRE.

By default, the `use_offline_repository` parameter is set to *true*. That means, your application will use the offline SapMachine JRE provided by the buildpack.

If you set this parameter to *false*, the buildpack will attempt to download SapMachine JRE of a particular version from the GitHub asset repository. This will only work if your Cloud Foundry instance has access to [GitHub: SapMachine](https://github.com/SAP/SapMachine).



### SapMachine 11

To point to the latest SapMachine JRE 11 version provided by the buildpack, specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
    JBP_CONFIG_SAP_MACHINE_JRE: '{ version: 11.+ }'
```

To make the buildpack download a particular published JRE version \(for example, 11.0.13\), specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
    JBP_CONFIG_SAP_MACHINE_JRE: '{use_offline_repository: false, version: 11.0.13 }'
  ...
```



### SapMachine 17

> ### Tip:  
> SAP Java Buildpack 1 and 2 provide a customized SapMachine JRE 17 that contains a [jdk.compiler](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.compiler/module-summary.html) module.

Use environment variable JBP\_CONFIG\_SAP\_MACHINE\_JRE in analogical way. For example:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
    JBP_CONFIG_SAP_MACHINE_JRE: '{ version: 17.+ }'
```

To make the buildpack download a particular published JRE version \(for example, 17.0.10\), specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
    JBP_CONFIG_SAP_MACHINE_JRE: '{use_offline_repository: false, version: 17.0.10 }'
  ...
```



### SapMachine 21

> ### Tip:  
> SAP Java Buildpack 2 provides a customized SapMachine JRE 21 that contains a [jdk.compiler](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.compiler/module-summary.html) module.

Use environment variable JBP\_CONFIG\_SAP\_MACHINE\_JRE in analogical way. For example:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
    JBP_CONFIG_SAP_MACHINE_JRE: '{ version: 21.+ }'
```

To make the buildpack download a particular published JRE version \(for example, 21.0.2\), specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
    JBP_CONFIG_SAP_MACHINE_JRE: '{use_offline_repository: false, version: 21.0.2 }'
  ...
```



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
> SapMachine JDK is **not bundled** within the buildpack. Therefore, if you want to use SapMachine JDK 11, 17 or 21, you have to download it from the [GitHub project](https://sap.github.io/SapMachine/) as an online component.
> 
> However, you can use the [jdk.compiler](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.compiler/module-summary.html) module, which is **provided** by the buildpack as part of the customized SapMachine JRE, v. 17 and 21. To learn more, see section [Activation Using JRE](sapmachine-785d6b3.md#loio785d6b390b834bee818e242160f87df5__section_jre).

To specify an online JDK version \(11, 17, or 21\), use environment variable JBP\_CONFIG\_SAP\_MACHINE\_JDK.



### SapMachine 11

To make the buildpack download a particular published JDK version \(for example, 11.0.22\), specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: '{ version: 11.0.22 }'
  ...
```

To point to the major version of the SapMachine JDK 11, specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: '{ version: 11.+ }'
```



### SapMachine 17

Use environment variable JBP\_CONFIG\_SAP\_MACHINE\_JDK in analogical way. For example:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: '{ version: 17.0.10 }'
  ...
```

To point to the major version of the SapMachine JDK 17, specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: '{ version: 17.+ }'
```



### SapMachine 21

Use environment variable JBP\_CONFIG\_SAP\_MACHINE\_JDK in analogical way. For example:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: '{ version: 21.0.2 }'
  ...
```

To point to the major version of the SapMachine JDK 21, specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: '{ version: 21.+ }'
```

**Related Information**  


[https://sap.github.io/SapMachine/](https://sap.github.io/SapMachine/)

[Runtimes and Containers](runtimes-and-containers-83d2416.md "Find out which application runtimes and containers you can use, depending on the Java buildpack your application is using.")

