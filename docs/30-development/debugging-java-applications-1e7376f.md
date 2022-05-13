<!-- loio1e7376fa1a8a4cefbed5c87693af4e6a -->

# Debugging Java Applications



Debugging an application helps you detect and diagnose errors in your code. You can control the execution of your program by setting breakpoints, suspending threads, stepping through the code, and examining the contents of the variables.

-   [Debug an Application Running on SAP JVM](debugging-java-applications-1e7376f.md#loioef7fbdb61ae44d83a96c0ba48e829032)

-   [Debug a Java Web Application Running on SapMachine](debugging-java-applications-1e7376f.md#loiof7fa9f367c644e34b87e6518f7724ccb)

-   [Debug an Application Running on Java SE](debugging-java-applications-1e7376f.md#loio0d6e305f08574bca811d42b55c3c0b47)


 <a name="loioef7fbdb61ae44d83a96c0ba48e829032"/>

<!-- loioef7fbdb61ae44d83a96c0ba48e829032 -->

## Debug an Application Running on SAP JVM

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


 <a name="loiof7fa9f367c644e34b87e6518f7724ccb"/>

<!-- loiof7fa9f367c644e34b87e6518f7724ccb -->

## Debug a Java Web Application Running on SapMachine

Debug an application running on a Cloud Foundry container that is using SapMachine.



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
    > Depending on what your SapMachine is using \(JRE or JDK\), specify the path accordingly \(**sap\_machine\_jre** or **sap\_machine\_jdk**\). To learn more, see: [SapMachine](customizing-the-java-virtual-machine-jvm-settings-b8cda61.md#loio785d6b390b834bee818e242160f87df5)

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
    > The connection is active until you close the SSH tunnel. When you finish debugging, close the SSH tunnel by pressing  [Ctrl\] + [C\] . Connect a Java debugger to your application. For example, use the standard Java debugger provided by Eclipse IDE and connect to `localhost:8000`


 <a name="loio0d6e305f08574bca811d42b55c3c0b47"/>

<!-- loio0d6e305f08574bca811d42b55c3c0b47 -->

## Debug an Application Running on Java SE

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


