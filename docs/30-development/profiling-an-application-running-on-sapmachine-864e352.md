<!-- loio864e35223c6b471ea72cd066ffe0608f -->

# Profiling an Application Running on SapMachine

You can use Java Flight Recorder \([JFR](https://openjdk.org/jeps/328)\) to profile your Java application on SapMachine, and Java Mission Control \([JMC](https://wiki.openjdk.org/display/jmc/Main)\) to do remote profiling and analysis.



<a name="loio864e35223c6b471ea72cd066ffe0608f__prereq_ntc_cng_4cb"/>

## Prerequisites

-   You have downloaded and installed a JDK Mission Control console. To do that, go to [SapMachine](https://sap.github.io/SapMachine/) → *Download* → *JMC 8*, select your operating system, and then choose *Download*.

-   You have installed the Cloud Foundry command line interface. See: [Download and Install the cf CLI](https://help.sap.com/docs/btp/sap-business-technology-platform/download-and-install-cloud-foundry-command-line-interface?version=Cloud)

-   You are logged on to a SAP BTP, Cloud Foundry space. See: [Log On to the Cloud Foundry Environment Using cf CLI](https://help.sap.com/docs/btp/sap-business-technology-platform/log-on-to-cloud-foundry-environment-using-cloud-foundry-command-line-interface?version=Cloud)

-   You have a Java application that is up and running on SAP BTP, Cloud Foundry.

-   You have enabled SSH for your application. See: [Configuring SSH access at the app level](https://docs.cloudfoundry.org/devguide/deploy-apps/ssh-apps.html#configure-ssh-access-apps)




<a name="loio864e35223c6b471ea72cd066ffe0608f__context_av2_4qd_gxb"/>

## Context

To profile with JMC, you need to start the Management Agent on a RMI port and then open an SSH tunnel to connect to that port. To do that, follow the steps below.

> ### Note:  
> In the steps below, we use **myapp** and **5555** as *exemplary* application name and port. Replace them with your actual app name and a free port number on your localhost.



<a name="loio864e35223c6b471ea72cd066ffe0608f__steps_yxl_nb3_fxb"/>

## Procedure

1.  Set the RMI server to `localhost`. To do that, set the following JBP\_CONFIG\_JAVA\_OPTS option in the `manifest.yml` file of your application:

    ```
    
    ---
    applications:
    - name: myapp
      buildpack: sap_java_buildpack
    ...
      env:
        TARGET_RUNTIME: tomcat
        JBP_CONFIG_COMPONENTS: "jres: ['com.sap.xs.java.buildpack.jre.SAPMachineJRE']"
        JBP_CONFIG_SAP_MACHINE_JRE: '{version: 11.+}'
        JBP_CONFIG_JAVA_OPTS: "[java_opts: '-Djava.rmi.server.hostname=127.0.0.1']"
    ```

2.  Start the Management Agent by running `jcmd` in your Cloud Foundry container. Execute:

    ```
    cf ssh myapp -c "app/META-INF/.sap_java_buildpack/sap_machine_jre/bin/jcmd $(pgrep java) ManagementAgent.start jmxremote.authenticate=false jmxremote.ssl=false jmxremote.port=5555 jmxremote.rmi.port=5555"
    ```

    Depending on what your SapMachine is using \(JRE or JDK\), specify the path accordingly \(**`sap_machine_jre`** or **`sap_machine_jdk`**\). To learn more, see: [SapMachine](sapmachine-785d6b3.md)

    **Result**:

    ```
    
    7:
    Command executed successfully
    
    ```

    Management Agent is started and is listening to port **5555**.

3.  \(Optional\) You can check the status of the Management Agent. Execute:

    ```
    cf ssh myapp -c "app/META-INF/.sap_java_buildpack/sap_machine_jre/bin/jcmd $(pgrep java) ManagementAgent.status"
    ```

4.  Enable an SSH tunnel for this port. Execute:

    ```
    cf ssh myapp -N -T -L 5555:127.0.0.1:5555
    ```

    Your *local* port 5555 is connected to the *remote* port 5555 of the JVM, which is running in the Cloud Foundry container.

    > ### Note:  
    > The connection is active until you close the SSH tunnel. When you finish profiling, close the SSH tunnel by pressing [Ctrl\] + [C\].

5.  Connect with JMC to `localhost:5555`. To do that:

    1.  Open your JDK Mission Control \(JMC\) console.

    2.  From, the *JVM Browser* tab, choose icon *Create a new custom JVM connection*.

    3.  For *Port*, enter ***5555*** \(or your actual port number\), and then choose *Finish*.


6.  In the left-side menu, a new node *localhost:5555* appears.

7.  Double-click on *MBean Server*.

8.  To start profiling, go to *Flight Recorder* and from its context menu, choose *Start Flight Recording*.

9.  Set up the event settings. From the drop-down menu, choose one of the following options \(templates\):

    -   *Continuous* – Low overhead configuration, safe for continuous use in production environments

    -   *Profiling* – Low overhead configuration for profiling

    -   *gc* – GC related events. Generates a small recording size.

    -   *gc\_details* – GC related events. Gets heap statistic and generates a large recording size.

    -   Create your own configuration. To do that, choose *Template Manager*, then select a predefined template and choose *Duplicate*. Rename the new template and edit its configuration parameters according to your needs and preferences.


10. After profiling is done, go to *localhost:5555* and from its context menu, choose *Disconnect*.

11. Then go back to your command line and close the SSH tunnel by pressing [Ctrl\] + [C\].

12. Stop the Management Agent. Execute:

    ```
    cf ssh myapp -c "app/META-INF/.sap_java_buildpack/sap_machine_jre/bin/jcmd $(pgrep java) ManagementAgent.stop"
    ```


**Related Information**  


[Debug an Application Running on SapMachine](debug-an-application-running-on-sapmachine-f7fa9f3.md "Debug a Java web application running on a Cloud Foundry container that is using SapMachine.")

