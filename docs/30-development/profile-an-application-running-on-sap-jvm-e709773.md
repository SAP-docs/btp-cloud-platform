<!-- loioe7097737709842b7bb1c3b9bf3d688b6 -->

# Profile an Application Running on SAP JVM

The SAP JVM Profiler is a tool that helps you analyze the resource consumption of a Java application running on SAP Java Virtual Machine \(JVM\). You can use it to profile simple standalone Java programs or complex enterprise applications.



<a name="loioe7097737709842b7bb1c3b9bf3d688b6__prereq_ntc_cng_4cb"/>

## Prerequisites

-   Install the SAP JVM Tools for Eclipse. For more information, see [Install the SAP JVM Tools in Eclipse](install-the-sap-jvm-tools-in-eclipse-6321379.md).

-   Open a debugging connection using an SSH tunnel. For more information, see [Debug an Application Running on SAP JVM](debug-an-application-running-on-sap-jvm-ef7fbdb.md)




## Context

To measure resource consumption, the SAP JVM Profiler enables you to run different profiling analyses. Each profiling analysis creates profiling events that focus on different aspects of resource consumption. For more information about the available analyses, see the SAP JVM Profiler documentation in Eclipse. Go to *Help* \> *Help Contents* \> *SAP JVM Profiler*.



## Procedure

1.  In Eclipse, open the *Profiling* perspective.

2.  From the *VM Explorer* view, choose ![](images/Connect_Host_Via_Debugging_Port_38d0768.png) \(*Connect Host Via Debugging Port*\).

3.  Enter your host name and port number, and choose *Next*.

    > ### Note:  
    > Your port number is your local SSH tunnel endpoint.

4.  Choose the analysis you want to run and specify your profiling parameters.

    > ### Note:  
    > To use the thread annotation filters, complete the fields under the *Analysis Options* section. By default, all filters are set to \*, which means that all annotations pass the filter.


