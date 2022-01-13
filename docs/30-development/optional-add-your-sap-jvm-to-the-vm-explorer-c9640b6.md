<!-- loioc9640b6bc22b43da8ec1b805f199e9ca -->

# \(Optional\) Add your SAP JVM to the VM Explorer

You can add your SAP JVM to the *VM Explorer* view of the SAP JVM Profiler.



<a name="loioc9640b6bc22b43da8ec1b805f199e9ca__prereq_t3z_fnh_4cb"/>

## Prerequisites

-   Install the SAP JVM Tools for Eclipse. For more information, see [Install the SAP JVM Tools in Eclipse](install-the-sap-jvm-tools-in-eclipse-6321379.md).

-   Download and install the Cloud Foundry Command Line Interface \(cf CLI\) and log on to Cloud Foundry. For more information, see [Download and Install the Cloud Foundry Command Line Interface](../50-administration-and-ops/download-and-install-the-cloud-foundry-command-line-interface-4ef907a.md) and [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](../50-administration-and-ops/log-on-to-the-cloud-foundry-environment-using-the-cloud-foundry-command-line-interface-7a37d66.md).




## Context

From the *VM Explorer,* you can debug, monitor or profile your SAP JVM. For more information about the *VM Explorer*, see the SAP JVM Profiler documentation in Eclipse. Go to *Help* \> *Help Contents* \> *SAP JVM Profiler*.

> ### Note:  
> You need to use the **jvmmond** tool, which is included in the SAP Java Buildpack.



## Procedure

1.  From the cf CLI, execute:

    ```
    cf ssh app name -c "app/META-INF/.sap_java_buildpack/sapjvm/bin/jvmmond -port 50003 -J-Dcom.sap.jvm.tools.portRange=50004-50005 -J-Djava.rmi.server.hostname=127.0.0.1"
    ```

    This starts the `jvmmond` service on your Cloud Foundry container. It is listening to port 50003. This command also specifies a port range of 50004-50005 in case additional ports need to be opened.

2.  To enable an SSH tunnel for these ports, execute:

    ```
    `cf ssh app name -N -T -L 50003:127.0.0.1:50003 -L 50004:127.0.0.1:50004 -L 50005:127.0.0.1:50005`
    ```

3.  In your Eclipse IDE, open the *Profiling* perspective, and from the *VM Explorer* view choose *Manage Hosts*.

4.  Choose *Add* and enter the following host name and port number: ***localhost:50003***




<a name="loioc9640b6bc22b43da8ec1b805f199e9ca__result_q2v_czh_zrb"/>

## Results

Your application is added to the VM Explorer.

