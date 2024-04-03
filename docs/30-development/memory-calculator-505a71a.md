<!-- loio505a71ae53e84c7a972bb6c34b4316fb -->

# Memory Calculator

The memory calculator provides a mechanism to fine-tune the Java Virtual Machine \(JVM\) memory for an application. Its goal is to ensure that applications perform well while not exceeding a container's memory limit.

Below you can find which memory calculators are used in the relevant Java buildpacks.



<a name="loio505a71ae53e84c7a972bb6c34b4316fb__section_kyg_nz3_k1c"/>

## SAP Java Buildpack 1

This buildpack supports two memory calculator versions:

-   [Memory Calculator V2](memory-calculator-v2-8eef959.md) – activated by default.

-   [Memory Calculator V1 \(SAP JVM Memory Calculator\)](memory-calculator-v1-sap-jvm-memory-calculator-c1059e0.md) – this is an optional memory calculator. You can activate it by adding the following environment variable:

    ```
    ---
    applications:
    - name: <app-name>
      ...
      env:
        MEMORY_CALCULATOR_V1: true
      ...
    ```




<a name="loio505a71ae53e84c7a972bb6c34b4316fb__section_qqb_4z3_k1c"/>

## SAP Java Buildpack 2

This buildpack supports only [Memory Calculator V2](memory-calculator-v2-8eef959.md), which is the same as the one provided by the community Java Buildpack. See: [\(GitHub\) Java Buildpack Memory Calculator](https://github.com/cloudfoundry/java-buildpack-memory-calculator)

> ### Note:  
> Memory Calculator V1 is deprecated \(not available\) for SAP Java Buildpack 2. If you try to activate it by setting the MEMORY\_CALCULATOR\_V1 environment variable, an error message will be thrown.



## Community Java Buildpack

This buildpack uses its default and only memory calculator: [\(GitHub\) Java Buildpack Memory Calculator](https://github.com/cloudfoundry/java-buildpack-memory-calculator) 

**Related Information**  


[Buildpacks](buildpacks-5e7fc02.md "")

