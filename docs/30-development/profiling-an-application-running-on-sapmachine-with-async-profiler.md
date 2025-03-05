
# Profiling an Application Running on SapMachine with async-profiler

You can use async-profiler \([asprof](https://github.com/async-profiler/async-profiler/blob/master/README.md)\) to profile your Java application on SapMachine.




## Prerequisites

-   You have to run your application on SapMachine 17.0.14 or 21.0.6, which is part of the SAP Java Buildpack 1.110.0 and 2.24.0.

-   You have installed the Cloud Foundry command line interface. See: [Download and Install the cf CLI](https://help.sap.com/docs/btp/sap-business-technology-platform/download-and-install-cloud-foundry-command-line-interface?version=Cloud)

-   You have installed the Cloud Foundry Java plugin for the Cloud Foundry command line interface. See: [Download and Install the cf Java plugin](https://help.sap.com/docs/btp/sap-business-technology-platform/cf-cli-plug-ins?&version=Cloud).

-   You are logged on to a SAP BTP, Cloud Foundry space. See: [Log On to the Cloud Foundry Environment Using cf CLI](https://help.sap.com/docs/btp/sap-business-technology-platform/log-on-to-cloud-foundry-environment-using-cloud-foundry-command-line-interface?version=Cloud)

-   You have a Java application that is up and running on SAP BTP, Cloud Foundry.

-   You have enabled SSH for your application. See: [Configuring SSH access at the app level](https://docs.cloudfoundry.org/devguide/deploy-apps/ssh-apps.html#configure-ssh-access-apps)





## Context

To profile with async-profiler, you can use the Cloud Foundry Java plugin. It provides some convenience commands for profiling. To do that, follow the steps below.

> ### Note:  
> In the steps below, we use **myapp** as *exemplary* application name. Replace them with your actual app name.




## Procedure

1.	Start CPU profiling. Execute:

    ```
    cf java start-asprof-cpu-profile myapp
    ```
    
    **Result**:

    ```
    
    Profiling started
    
    ```

2.  \(Optional\) You can check the status of the profiling. Execute:

    ```
    cf java asprof-status myapp
    ```

     **Result**:

    ```
    
    Profiling is running for xx seconds
    
    ```

3.  Stop profiling and download the profiling data to the given local-dir. Execute:

    ```
    cf java stop-asprof -local-dir . myapp
    ```

    **Result**:

    ```
    
    --- Execution profile ---
    Total samples       : 15
    ...

    Successfully created JFR recording in application container at: /tmp/myapp-<GUID>.jfr
    Jfr recording file saved to: ./myapp-asprof-<GUID>.jfr
    Jfr recording file deleted in app container
    
    ```


4.  Check with cf java the additional convenience commands. To profile other events you can start async-profiler by executing the start-asprof with arguments. Execute:

    ```
    cf java start-asprof --args "-e nativemem" myapp
    ```


**Related Information**  


[Profiling modes](https://github.com/async-profiler/async-profiler/blob/master/docs/ProfilingModes.md)

[Profiler options](https://github.com/async-profiler/async-profiler/blob/master/docs/ProfilerOptions.md)

