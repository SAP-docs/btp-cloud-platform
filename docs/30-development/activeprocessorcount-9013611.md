<!-- loio90136110179346a79c9cc2f0cc527333 -->

# ActiveProcessorCount

This JVM option overrides the number of CPUs which the virtual machine uses to calculate the size of thread pools for operations \(such as garbage collection\).

> ### Note:  
> Previously, SAP Java Buildpack used to set JVM option `"-XX:+UseContainerCpuShares"` but it's now replaced by **"-XX:ActiveProcessorCount=<value\>"**.

The `ActiveProcessorCount` flag prevents out-of-memory \(OOM\) errors in case a GC algorithm with high internal memory usage has been activated by the JVM in relatively small containers \(< 4GB\). Larger containers \(\>4GB\) benefit from a higher `ActiveProcessorCount` value.

SAP Java Buildpack automatically sets the JVM option `"-XX:ActiveProcessorCount=<value>"`, where **<value\>** is defined as follows:

-   For container instances < 4GB, the `ActiveProcessorCount` is set to **1**.

-   For container instances \>= 4GB, the `ActiveProcessorCount` is set to 1 CPU per 1GB of container memory. For example, if a container instance is 7GB, the value will be set to **7**.


If you want to explicitly set the value of `ActiveProcessorCount`, you can do that through the JBP\_CONFIG\_JAVA\_OPTS property in the application's *manifest.yml* file.

-   For SAP Java Buildpack 1:

    ```
    ---
    applications:
    - name: <APP_NAME>
      buildpacks:
      - sap_java_buildpack
      env:
        JBP_CONFIG_JAVA_OPTS: 'java_opts: ''-XX:ActiveProcessorCount=7'''
      ...
    ```

-   For SAP Java Buildpack 2:

    ```
    ---
    applications:
    - name: <APP_NAME>
      buildpacks:
      - sap_jakarta_buildpack
      env:
        JBP_CONFIG_JAVA_OPTS: 'java_opts: ''-XX:ActiveProcessorCount=7'''
      ...
    ```


**Related Information**  


[Out-Of-Memory Behavior](out-of-memory-behavior-588cfd9.md "")

