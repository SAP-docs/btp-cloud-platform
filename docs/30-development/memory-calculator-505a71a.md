<!-- loio505a71ae53e84c7a972bb6c34b4316fb -->

# Memory Calculator

The memory calculator provides a mechanism to fine-tune the Java Virtual Machine \(JVM\) memory for an application. Its goal is to ensure that applications perform well while not exceeding a container's memory limit.

Both SAP Java Buildpack and the Community Java Buildpack use [\(GitHub\) Java Buildpack Memory Calculator](https://github.com/cloudfoundry/java-buildpack-memory-calculator), also known as *Memory Calculator v2*.

There are three memory types, which can be sized - **stack\_threads**, **class\_count**, and **headroom**.

Customize the memory options by using the `JBP_CONFIG_JAVA_OPTS` environment variable:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_JAVA_OPTS: "[java_opts: '-Xms144M -Xss3M -Xmx444444K -XX:MetaspaceSize=66666K -XX:MaxMetaspaceSize=88888K']"
```



<a name="loio505a71ae53e84c7a972bb6c34b4316fb__section_olg_1d5_2wb"/>

## Default Settings

SAP Java Buildpack is delivered with a default built-in configuration of the memory sizing options in YML format - see the configuration files in the table below. These configuration files are parsed during application staging, and the memory configuration specified in them is used for calculating the memory sizes of `stack_threads`, `class_count`, and `headroom`.

Default structures of the relevant configuration files:


<table>
<tr>
<td valign="top">

`config/sap_machine_jre.yml`

</td>
<td valign="top">

> ### Sample Code:  
> ```
> 
> # Configuration for JRE repository
> ---
> 
> repository_root: "https://sapmachine.io/assets/cf/jre/{platform}/{architecture}"
> version: 21.+
> use_offline_repository: true
> repository_root_offline: "{default.repository.root}/sap_machine_jre/{platform}/{architecture}"
> memory_calculator_v2:
>   version: 1.+
>   repository_root: "{default.repository.root}/memory-calculator/{platform}/{architecture}"
>   class_count: 
>   headroom: 0
>   stack_threads: 250
> jvmkill_agent:
>   version: 1.+
>   repository_root: "{default.repository.root}/jvmkill/{platform}/{architecture}"
> ```



</td>
</tr>
<tr>
<td valign="top">

`config/sap_machine_jdk.yml`

</td>
<td valign="top">

> ### Sample Code:  
> ```
> 
> # Configuration for JDK repository
> ---
> 
> repository_root: "https://sapmachine.io/assets/cf/jdk/{platform}/{architecture}"
> version: 21.+
> repository_root_offline: "{default.repository.root}/sap_machine_jre/{platform}/{architecture}"
> memory_calculator_v2:
>   version: 1.+
>   repository_root: "{default.repository.root}/memory-calculator/{platform}/{architecture}"
>   class_count: 
>   headroom: 7
>   stack_threads: 250
> jvmkill_agent:
>   version: 1.+
>   repository_root: "{default.repository.root}/jvmkill/{platform}/{architecture}"
> ```



</td>
</tr>
</table>

The **memory\_calculator\_v2** section encloses the input data for the memory calculation techniques utilized in determining the JVM memory sizing options.

-   `stack_threads` – the number of threads to be used by the application. Default value: **250**
-   `headroom` – the percentage of the container's total memory \(available to the application\) that can be excluded from the memory calculator’s algorithm and used for covering JVM overhead \(non-JVM operations\). The maximum recommended value for headroom is **10**. Default value: **0**
-   `class_count` – the number of classes to be loaded. Default behavior: Estimating the number of class names in the application, adding a constant `42,215` to it, and then multiplying the final result by **0.35**. If you set a particular number, for example 500, only 500 classes will be loaded.

You can customize two memory options, by using the relevant environment variables:

-   JBP\_CONFIG\_SAP\_MACHINE\_JRE

-   JBP\_CONFIG\_SAP\_MACHINE\_JDK




## Java 25

> ### Note:  

If you need JRE with Java 25, you use SapMachine 25. Customize your memory options as follows:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
    JBP_CONFIG_SAP_MACHINE_JRE: "[version: 25.+, memory_calculator_v2: {stack_threads: 266, class_count: 1001, headroom: 5}]"

```

If you want to point to the SapMachine JDK component, you need to provide a specific version as follows:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: "[ version: 25.0.4, memory_calculator_v2: {stack_threads: 266, class_count: 1001, headroom: 5}]"
```

You can also point to the major version of the SapMachine JDK, in order to always get the latest patch versions. In this case, specify it the following way:

```
---
applications:
- name: <app-name>
  ...
  env:
    JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jdk.SAPMachineJDK']"
    JBP_CONFIG_SAP_MACHINE_JDK: "[ version: 25.+, memory_calculator_v2: {stack_threads: 266, class_count: 1001, headroom: 5}]"
```



<a name="loio505a71ae53e84c7a972bb6c34b4316fb__section_yyz_sh1_v1c"/>

## Java 21

> ### Note:  

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
    JBP_CONFIG_SAP_MACHINE_JDK: "[ version: 21.0.12, memory_calculator_v2: {stack_threads: 266, class_count: 1001, headroom: 5}]"
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



<a name="loio505a71ae53e84c7a972bb6c34b4316fb__section_pqx_vmp_q1c"/>

## Java 17

> ### Note:  

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
    JBP_CONFIG_SAP_MACHINE_JDK: "[ version: 17.0.20, memory_calculator_v2: {stack_threads: 266, class_count: 1001, headroom: 5}]"
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

[SapMachine](sapmachine-785d6b3.md "SapMachine provides a Java Runtime Environment (JRE) with Java 21 and 25.")

