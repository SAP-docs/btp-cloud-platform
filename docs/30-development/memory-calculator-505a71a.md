<!-- loio505a71ae53e84c7a972bb6c34b4316fb -->

# Memory Calculator

The memory calculator provides a mechanism to fine tune the Java Virtual Machine \(JVM\) memory for an application. Its goal is to ensure that applications perform well while not exceeding a container's memory limit.

Below you can find which memory calculators are used in the relevant Java buildpacks.



<a name="loio505a71ae53e84c7a972bb6c34b4316fb__section_kyg_nz3_k1c"/>

## SAP Java Buildpack

This buildpack supports two memory calculator versions:

-   [Memory Calculator V2](memory-calculator-v2-8eef959.md) – activated by default.

-   [Memory Calculator V1 \(SAP JVM Memory Calculator\)](memory-calculator-v1-sap-jvm-memory-calculator-c1059e0.md) – this is an optional memory calculator and you can activate by adding the following environment variable:

    ```
    ---
    applications:
    - name: <app-name>
      ...
      env:
        MEMORY_CALCULATOR_V1: true
      ...
    ```




## Community Java Buildpack

This buildpack uses its default and only memory calculator: [cloudfoundry/java-buildpack-memory-calculator](https://github.com/cloudfoundry/java-buildpack-memory-calculator) 

**Related Information**  


[Buildpacks](buildpacks-5e7fc02.md "")

