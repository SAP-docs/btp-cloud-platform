<!-- loiof7fa9f367c644e34b87e6518f7724ccb -->

# Debug an Application Running on SapMachine

Debug a Java web application running on a Cloud Foundry container that uses SapMachine.



<a name="loiof7fa9f367c644e34b87e6518f7724ccb__prereq_ih3_1v5_gjb"/>

## Prerequisites

-   [Download and Install the Cloud Foundry Command Line Interface](../50-administration-and-ops/download-and-install-the-cloud-foundry-command-line-interface-4ef907a.md)

-   [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](../50-administration-and-ops/log-on-to-the-cloud-foundry-environment-using-the-cloud-foundry-command-line-interface-7a37d66.md)




## Context

To debug an application using [SapMachine](https://github.com/SAP/SapMachine), you need to open a debugging port on your Cloud Foundry container, and then open an SSH tunnel to connect to that port.



## Procedure

1.  To open the debugging port, you need to configure the `JAVA_OPTS` parameter in your JVM. By default, the *agentlib* \(which enables the debugging\) is pre-configured. It could be turned off by setting the following property in the environment:

    ```
    env
    ...
      JBP_CONFIG_SAP_MACHINE_JDK: "[default_debug_agent_active: false]"
    ```

    You could also disable the default configuration by specifying it manually. Set the following option in the application `manifest.yml` file:

    ```
    JBP_CONFIG_JAVA_OPTS: "[java_opts: '-agentlib:jdwp=transport=dt_socket,address=8000,server=y,suspend=n]"
    ```

    You can change the default port **8000** in the command.

2.  To enable SSH tunneling in your application, run:

    ```
    cf enable-ssh <app_name>
    ```

3.  To open the SSH tunnel, run:

    ```
    cf ssh <app name> -N -T -L 8000:127.0.0.1:8000
    ```

    Your local port 8000 is connected to the debugging port 8000 of the JVM, which is running in the Cloud Foundry container.

    > ### Note:  
    > The connection is active until you close the SSH tunnel. When you finish debugging, close the SSH tunnel by pressing [Ctrl\] + [C\] .

4.  Connect a Java debugger to your application. For example, use the standard Java debugger provided by Eclipse IDE and connect to `localhost:8000`.


