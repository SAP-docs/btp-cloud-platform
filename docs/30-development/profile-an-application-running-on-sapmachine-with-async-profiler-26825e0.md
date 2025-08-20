<!-- loio26825e02b0a54271bb06b71f71a74d1e -->

# Profile an Application Running on SapMachine with async-profiler

You can use the [async-profiler](https://github.com/async-profiler/async-profiler/blob/master/README.md) tool to profile your Java application on SapMachine.



<a name="loio26825e02b0a54271bb06b71f71a74d1e__prereq_sgr_4d3_1fc"/>

## Prerequisites

-   You have installed the Cloud Foundry command line interface. See: [Download and Install the cf CLI](https://help.sap.com/docs/btp/sap-business-technology-platform/download-and-install-cloud-foundry-command-line-interface?version=Cloud)

-   You are logged on to a SAP BTP, Cloud Foundry space. See: [Log On to the Cloud Foundry Environment Using cf CLI](https://help.sap.com/docs/btp/sap-business-technology-platform/log-on-to-cloud-foundry-environment-using-cloud-foundry-command-line-interface?version=Cloud)

-   The version of your buildpack is at least **1.110.0** \(for SAP Java Buildpack 1\) or **2.24.0** \(for SAP Java Buildpack 2\).

-   The version of your SapMachine is at least **17.0.14** or **21.0.6**.

-   You have a Java application that is up and running on SAP BTP, Cloud Foundry.

-   You have enabled SSH for your application. See: [Configuring SSH access at the app level](https://docs.cloudfoundry.org/devguide/deploy-apps/ssh-apps.html#configure-ssh-access-apps)




<a name="loio26825e02b0a54271bb06b71f71a74d1e__context_av2_4qd_gxb"/>

## Context

To profile Java applications with the **`async-profiler`** tool, you can use the [cf CLI Java plugin](../50-administration-and-ops/java-plugin-for-cloud-foundry-command-line-interface-7677e79.md), which provides convenience commands for profiling.

> ### Note:  
> In the steps below, we use **myapp** as an *exemplary* application name. Replace it with your actual application name.



<a name="loio26825e02b0a54271bb06b71f71a74d1e__steps_yxl_nb3_fxb"/>

## Procedure

1.  Start the CPU profiling. Run:

    ```
    cf java asprof-start-cpu myapp
    ```

    **Result:** `Profiling started`

2.  \(Optional\) You can check the status of the profiling. Run:

    ```
    cf java asprof-status myapp
    ```

    **Result:** `Profiling is running for xx seconds`

3.  Stop profiling and download the profiling data to the given local directory. Run:

    ```
    cf java asprof-stop myapp
    ```

    **Result:** 

    ```
    
    --- Execution profile ---
    Total samples       : 15
    ...
    
    Successfully created JFR recording in application container at: /tmp/myapp-<GUID>.jfr
    Jfr recording file saved to: ./myapp-asprof-<GUID>.jfr
    Jfr recording file deleted in app container
    ```

4.  Check the additional convenience commands. Run:

    ```
    cf java
    ```

5.  To profile other events, you can start the *async-profiler* by running the `start-asprof` command with arguments:

    ```
    cf java asprof-start --args "-e nativemem" myapp
    ```


**Related Information**  


[Profiling Modes](https://github.com/async-profiler/async-profiler/blob/master/docs/ProfilingModes.md)

[Profiler Options](https://github.com/async-profiler/async-profiler/blob/master/docs/ProfilerOptions.md)

[Cloud Foundry Command Line Java plugin](https://github.com/SAP/cf-cli-java-plugin/blob/master/README.md)

