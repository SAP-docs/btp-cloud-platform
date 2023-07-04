<!-- loio785d6b390b834bee818e242160f87df5 -->

# SapMachine



<a name="loio785d6b390b834bee818e242160f87df5__section_pt4_b32_vsb"/>

## Context

[SapMachine](https://sap.github.io/SapMachine/) is an alternative to SAP JVM. It provides a Java Runtime Environment \(JRE\) with Java 11, while SAP JVM provides a JRE with Java 8.

SapMachine works only with [Tomcat](tomcat-ddfc101.md) and [Java Main](java-main-8a1786a.md) application containers.



<a name="loio785d6b390b834bee818e242160f87df5__section_lly_ftm_33b"/>

## Activation



### Using JRE

To activate SapMachine **JRE** \(instead of the default SAPJVM JRE\) in SAP Java Buildpack, you have to add the following environment variable:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
  ...
```

This will make your application use the SapMachine JRE 11 version bundled with SAP Java Buildpack.

Alternatively, you can direct the buildpack to download any published SapMachine patch version by adding additional configuration parameters, like the following:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
    JBP_CONFIG_SAP_MACHINE_JRE: '{ use_offline_repository: false, version: 11.0.13 }'
  ...
```

Setting `use_offline_repository` to *false* will direct the buildpack to attempt a download of the SapMachine JRE of version "`<version>`" from the GitHub asset repository. This will only work if your Cloud Foundry instance has access to [GitHub: SapMachine](https://github.com/SAP/SapMachine).



### Using JDK

Furthermore, you can also use a full SapMachine **JDK**:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
  ...
```

To specify the JDK version, use environment variable JBP\_CONFIG\_SAP\_MACHINE\_JDK. For example:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: '{ version: 11.0.15 }'
  ...
```

You can also point to the major version of the SapMachine JDK, in order to always get the latest patch versions. In this case, specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: "{ version: 11.+ }"
```

> ### Restriction:  
> As the SapMachine JDK is not bundled into the SAP Java Buildpack, you will always have to download it from GitHub as an online component.

**Related Information**  


[Tomcat](tomcat-ddfc101.md "By default, web applications deployed with SAP Java Buildpack are running in an Apache Tomcat container.")

[Java Main](java-main-8a1786a.md "You can create a Java application that starts its own runtime. This allows the usage of frameworks and Java runtimes, such as Spring Boot, Jetty, Undertow, or Netty.")

[https://sap.github.io/SapMachine/](https://sap.github.io/SapMachine/)

