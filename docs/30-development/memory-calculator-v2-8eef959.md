<!-- loio8eef9590a1d24e87af239d7c7e15fffe -->

# Memory Calculator V2



<a name="loio8eef9590a1d24e87af239d7c7e15fffe__section_ytm_f2x_42b"/>

## Manual Memory Customization

Customize the memory options by using the `JBP_CONFIG_JAVA_OPTS` environment variable:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_JAVA_OPTS: "[java_opts: '-Xms144M -Xss3M -Xmx444444K -XX:MetaspaceSize=66666K -XX:MaxMetaspaceSize=88888K']"
```



<a name="loio8eef9590a1d24e87af239d7c7e15fffe__section_olg_1d5_2wb"/>

## Automatic Memory Customization

The *memory\_calculator\_v2* section in the [config/sapjvm.ym](memory-calculator-v1-sap-jvm-memory-calculator-c1059e0.md#loioc1059e056aad406297addcd177a4fb7c__sap-samplecodeblock_ob1_fnk_r2b) configuration file has three sizing options:

-   `stack_threads` – an estimate of the number of threads that will be used by the application
-   `class_count` – an estimate of the number of classes that will be loaded
-   `headroom` – percentage of total memory available that is unallocated to cover JVM overhead. Maximum recommended value for headroom is **10**. Default value \(if not specified\) is **0**.

Depending on which Java version you use \(8 or 11\), you can customize these three memory options by using the relevant environment variables:

-   JBP\_CONFIG\_SAPJVM

-   JBP\_CONFIG\_SAP\_MACHINE\_JRE

-   JBP\_CONFIG\_SAP\_MACHINE\_JDK




<a name="loio8eef9590a1d24e87af239d7c7e15fffe__section_pl2_pk2_c5b"/>

## Java 8

> ### Note:  
> Only relevant for SAP Java Buildpack 1

If you need JRE with Java 8, you have to use SAP JVM. Customize your memory options as follows:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_SAPJVM: "[memory_calculator_v2: {stack_threads: 266, class_count: 1001, headroom: 5}]"
    
```



<a name="loio8eef9590a1d24e87af239d7c7e15fffe__section_ucx_wk2_c5b"/>

## Java 11

> ### Note:  
> Only relevant for SAP Java Buildpack 1

If you need JRE with Java 11, you have to use SapMachine 11. Customize your memory options as follows:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
    JBP_CONFIG_SAP_MACHINE_JRE: "[version: 11.+, memory_calculator_v2: {stack_threads: 266, class_count: 1001, headroom: 5}]"
```

If you want to point to the SapMachine JDK component, you need to provide a specific version as follows:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: "[ version: 11.0.15, memory_calculator_v2: {stack_threads: 266, class_count: 1001, headroom: 5}]"
```

You can also point to the major version of the SapMachine JDK, in order to always get the latest patch versions. In this case, specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: "[ version: 11.+, memory_calculator_v2: {stack_threads: 266, class_count: 1001, headroom: 5}]"
```



<a name="loio8eef9590a1d24e87af239d7c7e15fffe__section_pqx_vmp_q1c"/>

## Java 17

> ### Note:  
> Relevant for all Java buildpacks

If you need JRE with Java 17, you use SapMachine 17. Customize your memory options as follows:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
    JBP_CONFIG_SAP_MACHINE_JRE: "[version: 17.+, memory_calculator_v2: {stack_threads: 266, class_count: 1001, headroom: 5}]"

```

If you want to point to the SapMachine JDK component, you need to provide a specific version as follows:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: "[ version: 17.0.15, memory_calculator_v2: {stack_threads: 266, class_count: 1001, headroom: 5}]"
```

You can also point to the major version of the SapMachine JDK, in order to always get the latest patch versions. In this case, specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: "[ version: 17.+, memory_calculator_v2: {stack_threads: 266, class_count: 1001, headroom: 5}]"
```

**Related Information**  


[GitHub: Java Buildpack Memory Calculator](https://github.com/cloudfoundry/java-buildpack-memory-calculator)

[SapMachine](sapmachine-785d6b3.md "SapMachine is an alternative to SAP JVM, and provides a Java Runtime Environment (JRE) with Java 11 and 17.")

