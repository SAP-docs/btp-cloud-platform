<!-- loioef7fbdb61ae44d83a96c0ba48e829032 -->

# Debug an Application Running on SAP JVM

You can debug an application running on a Cloud Foundry container that is using SAP JVM. By using SAP JVM, you can enable debugging on-demand without having to restart the application or the JVM.



<a name="loioef7fbdb61ae44d83a96c0ba48e829032__prereq_ef3_52t_gcb"/>

## Prerequisites

-   [Download and Install the Cloud Foundry Command Line Interface](../50-administration-and-ops/download-and-install-the-cloud-foundry-command-line-interface-4ef907a.md) 

-   [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](../50-administration-and-ops/log-on-to-the-cloud-foundry-environment-using-the-cloud-foundry-command-line-interface-7a37d66.md)

-   Deploy your application using the SAP Java Buildpack. To do that, from the cf CLI execute:

    ```
    cf push <app name> -p <war file> -b sap_java_buildpack
    ```

-   Ensure that SSH is enabled for the application. See [Accessing Apps with SSH](https://docs.cloudfoundry.org/devguide/deploy-apps/ssh-apps.html) 


> ### Note:  
> SAP JVM is included in the SAP Java Buildpack. With SAP JVM, you can enable debugging on-demand. You do not need to set any debugging parameters.



## Context

After enabling the debugging port, you need to open an SSH tunnel, which connects to that port.



## Procedure

1.  To enable debugging or to check the debugging state of your JVM, run `jvmmon` in your Cloud Foundry container by executing:

    ```
    cf ssh <app name> -c "app/META-INF/.sap_java_buildpack/sapjvm/bin/jvmmon"
    ```

2.  From the `jvmmon` command line window, execute:

    ```
    start debugging
    ```

3.  \(Optional\) To confirm that debugging is enabled and see which port is open, execute:

    ```
    print debugging information
    ```

    The following is an example of the information displayed by `jvmmon`:

    ```
    State: Debugging back is waiting for debugger to connect
    Port: 8000
    Client:
    Globally accessible
    ```

    > ### Note:  
    > The default port is 8000.

4.  To exit `jvmmon`, execute: `q`

5.  From the cf CLI, open the SSH tunnel by executing:

    ```
    cf ssh <app name> -N -T -L 8000:127.0.0.1:8000
    ```

6.  Connect a Java debugger to your application. For example, use the standard Java debugger provided by Eclipse IDE and connect to `localhost:8000`


