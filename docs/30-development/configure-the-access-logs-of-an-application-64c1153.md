<!-- loio64c1153a9f9f4122932f4adc87abb3da -->

# Configure the Access Logs of an Application

The SAP Java Buildpack uses the *logback-access* module to provide HTTP-access log functionality.



<a name="loio64c1153a9f9f4122932f4adc87abb3da__prereq_gw2_v5j_4kb"/>

## Prerequisites

-    [Download and Install the Cloud Foundry Command Line Interface](../50-administration-and-ops/download-and-install-the-cloud-foundry-command-line-interface-4ef907a.md)

-   [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](../50-administration-and-ops/log-on-to-the-cloud-foundry-environment-using-the-cloud-foundry-command-line-interface-7a37d66.md)




## Context

The access logs differ slightly from the other logs and traces. There are many standard tools available that read access logs from any server, display them, calculate statistics and so on. That's why the format of the access log produced by Tomcat and TomEE 7 is not SAP-specific. The default pattern defined in the configuration file is `"%date "%r" %s %b"`.

To find the access log files of your application, you have to connect via SSH to the Cloud Foundry container and go to the `logs` directory.



## Procedure

1.  Modify the default configuration.

    SAP Java buildpack uses LogbackValve to configure access logs in Tomcat and TomEE 7. The following environment variables are used in the configuration file and can be overwritten:

    -   *<ACCESS\_LOG\_FILE\>*
    -   *<ACCESS\_LOG\_FILE\_COUNT\>*
    -   *<ACCESS\_LOG\_FILE\_MAX\_SIZE\>*
    -   *<logback.access.log.xs.pattern\>*

2.  \(Optional\) Change the name of the access log files.

    By default access logs are placed in the application container in the `logs/access.log` file. You can configure the directory containing this file and the name of the files – with the environment variable `ACCESS_LOG_FILE`. To do that, define the full path to the desired directory and the file name. For example:

    ```
    env:
        ACCESS_LOG_FILE: "/home/vcap/logs/access-log/access.log"
    ```

3.  \(Optional\) Change the number of access log files.

    You can change the number of stored files with the environment variable `ACCESS_LOG_FILE_COUNT`. The default value is **3**. For example:

    ```
    env:
        ACCESS_LOG_FILE_COUNT: 5
    ```

4.  \(Optional\) Change the size of the access log files.

    You can modify the size of every access log file with the environment variable `ACCESS_LOG_FILE_MAX_SIZE`. The default value is **8** MB. For example:

    ```
    env:
        ACCESS_LOG_FILE_MAX_SIZE: 10
    ```

5.  \(Optional\) Change the format of the HTTP access log

    You can change the default format and have your access logs written differently. The SAP Java buildpack uses the *Resource configuration* functionality to allow this. Changing the `pattern` attribute in the configuration file of Tomcat and TomEE 7 is supported. The application has to provide the new value via the JBP\_CONFIG mechanism:

    -   Changing the format of the access log for Tomcat:

        ```
        env:
        JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomcat/conf/logback-access-localhost.xml':{'logback.access.log.xs.pattern' : 'combined'}]"
        ```

    -   Changing the format of the access log for TomEE 7:

        ```
        env:
        JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomee7/conf/logback-access-localhost.xml':{'logback.access.log.xs.pattern' : 'combined'}]"
        ```



