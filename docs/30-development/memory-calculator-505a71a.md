<!-- loio505a71ae53e84c7a972bb6c34b4316fb -->

# Memory Calculator

The memory calculator provides a mechanism to fine tune the Java Virtual Machine \(JVM\) memory for an application. Its goal is to ensure that applications perform well while not exceeding a container's memory limit.

The SAP Java Buildpack provides two options for a memory calculator:

-   [Memory Calculator V2](memory-calculator-v2-8eef959.md) – this memory calculator is activated by default.

-   [Memory Calculator V1 \(SAP JVM Memory Calculator\)](memory-calculator-v1-sap-jvm-memory-calculator-c1059e0.md) – this is an optional memory calculator and could be activated with the following environment variable:

    ```
    ---
    applications:
    - name: <app-name>
      ...
      env:
        MEMORY_CALCULATOR_V1: true
      ...
    ```


