<!-- loiof7fa9f367c644e34b87e6518f7724ccb -->

# Debug an Application Running on SapMachine

Debug a Java web application running on a Cloud Foundry container that is using SapMachine.



<a name="loiof7fa9f367c644e34b87e6518f7724ccb__prereq_ih3_1v5_gjb"/>

## Prerequisites

-   [Download and Install the Cloud Foundry Command Line Interface](../50-administration-and-ops/download-and-install-the-cloud-foundry-command-line-interface-4ef907a.md)

-   [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](../50-administration-and-ops/log-on-to-the-cloud-foundry-environment-using-the-cloud-foundry-command-line-interface-7a37d66.md)




## Context

To debug an application using [SapMachine](https://github.com/SAP/SapMachine), you need to open a debugging port on your Cloud Foundry container, and then open an SSH tunnel to connect to that port.



## Procedure

1.  To open the debugging port, you need to configure the `JAVA_OPTS` parameter in your JVM. By default, the *agentlib*, which enables the debug is pre-configured. It could be turned off by setting the following property in the environment:

    ```
    env
    ...
      JBP_CONFIG_SAP_MACHINE_JDK: "[default_debug_agent_active: false]"
    ```

    You could also disable the default configuration by specifying it manually. Set the following option in the application manifest file:

    ```
    JBP_CONFIG_JAVA_OPTS: "[java_opts: '-agentlib:jdwp=transport=dt_socket,address=8000,server=y,suspend=n,onjcmd=y']"
    ```

    You can change the default port 8000 in the command.

2.  To enable debugging or to check the debugging state of your JVM, run *jcmd* in your Cloud Foundry container. Execute:

    ```
    cf ssh <app name> -c "export JAVA_PID=`ps -C java -o pid=` && app/META-INF/.sap_java_buildpack/sap_machine_jdk/bin/jcmd $JAVA_PID VM.start_java_debugging"
    ```

    > ### Note:  
    > Depending on what your SapMachine is using \(JRE or JDK\), specify the path accordingly \(**sap\_machine\_jre** or **sap\_machine\_jdk**\). To learn more, see: [SapMachine](sapmachine-785d6b3.md)

    The following is an example of the information displayed by `jcmd`:

    ```
    <pid>:
    Debugging has been started.
    Transport : dt_socket
    Address : 8000
    ```

    > ### Note:  
    > The default port is 8000.

3.  To enable SSH tunneling in your application, execute:

    ```
    cf enable-ssh
    ```

4.  To open the SSH tunnel, execute:

    ```
    cf ssh <app name> -N -T -L 8000:127.0.0.1:8000
    ```

    Your local port 8000 is connected to the debugging port 8000 of the JVM, which running in the Cloud Foundry container.

    > ### Caution:  
    > The connection is active until you close the SSH tunnel. When you finish debugging, close the SSH tunnel by pressing [Ctrl\] + [C\] . Connect a Java debugger to your application. For example, use the standard Java debugger provided by Eclipse IDE and connect to `localhost:8000`


