<!-- loio505a71ae53e84c7a972bb6c34b4316fb -->

# Memory Calculator

The memory calculator provides a mechanism to fine-tune the Java Virtual Machine \(JVM\) memory for an application. Its goal is to ensure that applications perform well while not exceeding a container's memory limit.

Below you can find which memory calculators are used in the relevant Java buildpacks.



<a name="loio505a71ae53e84c7a972bb6c34b4316fb__section_qqb_4z3_k1c"/>

## SAP Java Buildpack 2

This buildpack supports only [Memory Calculator V2](memory-calculator-v2-8eef959.md), which is the same as the one provided by the community Java Buildpack. See: [\(GitHub\) Java Buildpack Memory Calculator](https://github.com/cloudfoundry/java-buildpack-memory-calculator)



<a name="loio505a71ae53e84c7a972bb6c34b4316fb__section_kyg_nz3_k1c"/>

## SAP Java Buildpack 1 – Deprecated!

This buildpack is no longer available. It used to support two memory calculator versions:

-   [Memory Calculator V2](memory-calculator-v2-8eef959.md) – activated by default.

-   [Memory Calculator V1 – DEPRECATED!](memory-calculator-v1-deprecated-c1059e0.md) – this was an optional memory calculator that could be activated by adding the following environment variable:

    ```
    ---
    applications:
    - name: <app-name>
      ...
      env:
        MEMORY_CALCULATOR_V1: true
      ...
    ```


> ### Restriction:  
> Memory Calculator V1 is no longer used. It was only available for [SAP Java Buildpack 1 – DEPRECATED!](sap-java-buildpack-1-deprecated-ad3e8df.md).



## Community Java Buildpack

This buildpack uses its default and only memory calculator: [\(GitHub\) Java Buildpack Memory Calculator](https://github.com/cloudfoundry/java-buildpack-memory-calculator) 

**Related Information**  


[Buildpacks](buildpacks-5e7fc02.md "")

