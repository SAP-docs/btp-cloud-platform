<!-- loio8eef9590a1d24e87af239d7c7e15fffe -->

# Memory Calculator V2



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

## Default Settings

SAP Java Buildpack is delivered with a default built-in configuration of the memory sizing options in YML format - **`config/sap_machine_jre.yml`** or **`config/sap_machine_jdk.yml`** \(path related to the buildpack archive\). These configuration files are parsed during application staging, and the memory configuration specified in them is used for calculating the memory sizes of *stack\_threads*, *class\_count* and *headroom*.

The default structure of the `config/sap_machine_jre.yml` configuration file, for example, is the following:

> ### Sample Code:  
> ```
> 
> config/sap_machine_jre.yml
> 
> 
> # Configuration for JRE repository
> ---
>   repository_root: "https://sap.github.io/SapMachine/assets/cf/jre/{platform}/{architecture}"
> jvmkill_agent:
>   version: 1.+
>   repository_root: "{default.repository.root}/jvmkill/{platform}/{architecture}"
> memory_calculator:
>   version: 3.+
>   repository_root: "{default.repository.root}/memory-calculator/{platform}/{architecture}"
>   class_count: 500 
>   headroom: 7
>   stack_threads: 250
> ```

-   `stack_threads` – an estimate of the number of threads that will be used by the application. Default value is **250**.
-   `class_count` – an estimate of the number of classes that will be loaded. The default behavior is to estimate this number as a fraction \(0.35\) of the number of class files in the application.
-   `headroom` – percentage of total memory available that is unallocated to cover JVM overhead. Maximum recommended value for headroom is **10**. Default value is **0**.

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
    JBP_CONFIG_SAP_MACHINE_JDK: "[ version: 11.0.22, memory_calculator_v2: {stack_threads: 266, class_count: 1001, headroom: 5}]"
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
    JBP_CONFIG_SAP_MACHINE_JDK: "[ version: 17.0.10, memory_calculator_v2: {stack_threads: 266, class_count: 1001, headroom: 5}]"
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



<a name="loio8eef9590a1d24e87af239d7c7e15fffe__section_yyz_sh1_v1c"/>

## Java 21

> ### Note:  
> Only relevant for SAP Java Buildpack 2

If you need JRE with Java 21, you use SapMachine 21. Customize your memory options as follows:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
    JBP_CONFIG_SAP_MACHINE_JRE: "[version: 21.+, memory_calculator_v2: {stack_threads: 266, class_count: 1001, headroom: 5}]"

```

If you want to point to the SapMachine JDK component, you need to provide a specific version as follows:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: "[ version: 21.0.2, memory_calculator_v2: {stack_threads: 266, class_count: 1001, headroom: 5}]"
```

You can also point to the major version of the SapMachine JDK, in order to always get the latest patch versions. In this case, specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: "[ version: 21.+, memory_calculator_v2: {stack_threads: 266, class_count: 1001, headroom: 5}]"
```

**Related Information**  


[GitHub: Java Buildpack Memory Calculator](https://github.com/cloudfoundry/java-buildpack-memory-calculator)

[SapMachine](sapmachine-785d6b3.md "SapMachine is an alternative to SAP JVM, and provides a Java Runtime Environment (JRE) with Java 11, 17, and 21.")

