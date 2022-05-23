<!-- loio0d6e305f08574bca811d42b55c3c0b47 -->

# Debug an Application Running on Java SE

You can debug an application running on a Cloud Foundry container that is using the standard Java community buildpack.



<a name="loio0d6e305f08574bca811d42b55c3c0b47__prereq_ih3_1v5_gjb"/>

## Prerequisites

-   [Download and Install the Cloud Foundry Command Line Interface](../50-administration-and-ops/download-and-install-the-cloud-foundry-command-line-interface-4ef907a.md)

-   [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](../50-administration-and-ops/log-on-to-the-cloud-foundry-environment-using-the-cloud-foundry-command-line-interface-7a37d66.md)




## Context

To debug an application, you need to open a debugging port on your Cloud Foundry container and open an SSH tunnel that will connect to that port.



## Procedure

1.  To open the debugging port, you need to configure the `JAVA_OPTS` parameter in your JVM. From the cf CLI, execute:

    ```
    cf set-env <app name> JAVA_OPTS '-Xrunjdwp:transport=dt_socket,server=y,suspend=n,address=8000'
    ```

2.  To enable SSH tunneling for your application, execute:

    ```
    cf enable-ssh <app name>
    ```

3.  To activate the previous changes, restart the application by executing:

    ```
    cf restart <app name>
    ```

4.  To open the SSH tunnel, execute:

    ```
    cf ssh <app name> -N -T -L 8000:127.0.0.1:8000
    ```

    Your local port 8000 is connected to the debugging port 8000 of the JVM running in the Cloud Foundry container.

    > ### Note:  
    > The default port is 8000.

    > ### Caution:  
    > The connection is active until you close the SSH tunnel. When you finish debugging, close the SSH tunnel by pressing  [Ctrl\] + [C\] .

5.  Connect a Java debugger to your application. For example, use the standard Java debugger provided by Eclipse IDE and connect to `localhost:8000`


