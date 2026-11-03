<!-- loio785d6b390b834bee818e242160f87df5 -->

# SapMachine

SapMachine provides a Java Runtime Environment \(JRE\) with Java 21 and 25.



It works with the following application containers:

-   [TomEE 10](tomee-10-66e808e.md)

-   [Tomcat 10](tomcat-10-97d0e34.md)

-   [Tomcat 11](tomcat-11-7c854a1.md)

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

By default, the `use_offline_repository` parameter is set to *true*. That means, your application will use the offline SapMachine JRE provided by the buildpack. Default version: **SapMachine JRE 21**

If you set this parameter to *false*, the buildpack will attempt to download SapMachine JRE of a particular version from the GitHub asset repository. This will only work if your Cloud Foundry instance has access to [GitHub: SapMachine](https://github.com/SAP/SapMachine).

To specify a particular JRE version, use environment variable JBP\_CONFIG\_SAP\_MACHINE\_JRE.



### SapMachine 25

> ### Tip:  
> SAP Java Buildpack provides a customized SapMachine JRE 25 that contains a [jdk.compiler](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.compiler/module-summary.html) module.

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

In some cases, it can be helpful to pin a particular published version of SapMachine JRE 25. To make the buildpack download this JRE version \(for example, 25.0.4\), specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
    JBP_CONFIG_SAP_MACHINE_JRE: '{use_offline_repository: false, version: 25.0.4 }'
  ...
```

**NOTE:** To stay secure, you need to update this version string on your own. For this reason, SAP does **not** recommend this approach.



### SapMachine 21

> ### Tip:  
> SAP Java Buildpack provides a customized SapMachine JRE 21 that contains a [jdk.compiler](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.compiler/module-summary.html) module.

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

In some cases, it can be helpful to pin a particular published version of SapMachine JRE 21. To make the buildpack download this JRE version \(for example, 21.0.12\), specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
    JBP_CONFIG_SAP_MACHINE_JRE: '{use_offline_repository: false, version: 21.0.12 }'
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
> SapMachine JDK is **not bundled** within the buildpack. Therefore, if you want to use SapMachine JDK 21 or 25, you have to download it from the [GitHub project](https://sapmachine.io/) as an online component.
> 
> However, you can use the [jdk.compiler](https://docs.oracle.com/en/java/javase/11/docs/api/jdk.compiler/module-summary.html) module, which is **provided** by the buildpack as part of the customized SapMachine JRE, v. 21 and 25. To learn more, see section [Activation Using JRE](sapmachine-785d6b3.md#loio785d6b390b834bee818e242160f87df5__section_jre).

To specify an online JDK version \(21 or 25\), use environment variable JBP\_CONFIG\_SAP\_MACHINE\_JDK.



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

In some cases, it can be helpful to pin a particular published version of SapMachine JDK 25. To make the buildpack download this JDK version \(for example, 25.0.4\), specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: '{ version: 25.0.4 }'
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

In some cases, it can be helpful to pin a particular published version of SapMachine JDK 21. To make the buildpack download this JDK version \(for example, 21.0.12\), specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: '{ version: 21.0.12 }'
  ...
```

**NOTE:** To stay secure, you need to update this version string on your own. For this reason, SAP does **not** recommend this approach.

**Related Information**  


[https://sapmachine.io/](https://sapmachine.io/)

[SAP Java Buildpack](sap-java-buildpack-1cf206b.md "SAP Java Buildpack is a Cloud Foundry buildpack for running SapMachine-based applications.")

[Runtimes and Containers](runtimes-and-containers-83d2416.md "Find out the available application runtimes and containers you can use for your Java applications.")

[Debug an Application Running on SapMachine](debug-an-application-running-on-sapmachine-f7fa9f3.md "Debug a Java web application running on a Cloud Foundry container that uses SapMachine.")

[Configure a Java Application for Logs and Traces](configure-a-java-application-for-logs-and-traces-5551c5e.md "Configure the collection of log and trace messages generated by a Java application in SAP BTP, Cloud Foundry.")

