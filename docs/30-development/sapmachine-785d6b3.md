<!-- loio785d6b390b834bee818e242160f87df5 -->

# SapMachine



<a name="loio785d6b390b834bee818e242160f87df5__section_pt4_b32_vsb"/>

## Context

[SapMachine](https://sap.github.io/SapMachine/) is an alternative to SAP JVM. It provides a Java Runtime Environment \(JRE\) with Java 11 and 17, while SAP JVM provides a JRE with Java 8. SapMachine works with the following application containers:

-   [Tomcat 9](tomcat-ddfc101.md)

-   [Java Main](java-main-8a1786a.md)

-   [TomEE 7.1](tomee-7-79c039a.md)

    > ### Note:  
    > Bear in mind that TomEE 7.1 supports only Java 7 and 8. Thus, even if your TomEE 7 application runs successfully with SapMachine JRE 17, at some point it might crash. Also, TomEE 7.1 has already [reached end of life](https://tomee.apache.org/tomee-7.1-eol.html). See also: [Discontinued TomEE versions](https://tomee.apache.org/download-discontinued.html)




<a name="loio785d6b390b834bee818e242160f87df5__section_lly_ftm_33b"/>

## Activation Using JRE



### SapMachine 11

To activate SapMachine **JRE** \(instead of the default SAP JVM JRE\) in SAP Java Buildpack, you have to add the following environment variable:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
  ...
```

This will make your application use the SapMachine JRE 11, bundled with SAP Java Buildpack.

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

You can also point to the major version of the SapMachine JRE 11, in order to always get the latest patch versions. In this case, specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
    JBP_CONFIG_SAP_MACHINE_JRE: "{ version: 11.+ }"
```



### SapMachine 17

Use environment variable JBP\_CONFIG\_SAP\_MACHINE\_JRE in analogical way. For example:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
    JBP_CONFIG_SAP_MACHINE_JRE: '{ version: 17.0.8 }'
  ...
```

To point to the major version of the SapMachine JRE 17, specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
    JBP_CONFIG_SAP_MACHINE_JRE: "{ version: 17.+ }"
```



<a name="loio785d6b390b834bee818e242160f87df5__section_b4d_ktv_jyb"/>

## Activation Using JDK

To use a full SapMachine **JDK**, use the following configurations:

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



### SapMachine 11

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

To point to the major version of the SapMachine JDK 11, specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: "{ version: 11.+ }"
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
    JBP_CONFIG_SAP_MACHINE_JDK: '{ version: 17.0.8 }'
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
    JBP_CONFIG_SAP_MACHINE_JDK: "{ version: 17.+ }"
```

> ### Restriction:  
> As the SapMachine JDK is not bundled into the SAP Java Buildpack, if you want to use SapMachine JDK 11 or 17, you have to download them from the [GitHub project](https://sap.github.io/SapMachine/) as an online component.

**Related Information**  


[Tomcat](tomcat-ddfc101.md "By default, web applications pushed with SAP Java Buildpack are running in an Apache Tomcat container.")

[TomEE 7](tomee-7-79c039a.md "By default, web applications deployed with SAP Java Buildpack are running in an Apache Tomcat container.")

[Java Main](java-main-8a1786a.md "You can create a Java application that starts its own runtime. This allows the usage of frameworks and Java runtimes, such as Spring Boot, Jetty, Undertow, or Netty.")

[https://sap.github.io/SapMachine/](https://sap.github.io/SapMachine/)

