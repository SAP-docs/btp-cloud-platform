<!-- loio604fdb57c97744a0b6bff91d503f99a8 -->

# Java Memory Assistant \[AWS, Azure, or GCP Regions\]

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

A Java agent that generates heap dumps based on preconfigured conditions in the memory usage of the application. See [Java Memory Assistant](https://github.com/SAP/java-memory-assistant).

When enabled in the buildpack, the agent will generate two files – `*.hprof` \(heap dump\) and `*.addons`, when the configured memory limits are met. The \*.addons file contains:

-   command line parameters

-   the implemented interfaces for the classes

-   information \(name\) about transient fields for the classes

-   a class and metaspace statistic

-   stack traces of the last OOM errors


See [Java Memory Assistant Framework](https://github.com/cloudfoundry/java-buildpack/blob/master/docs/framework-java_memory_assistant.md).

