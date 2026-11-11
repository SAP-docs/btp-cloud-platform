<!-- loio604fdb57c97744a0b6bff91d503f99a8 -->

# Java Memory Assistant \[AWS, Azure, or GCP Regions\]

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

Java Memory Assistant is a Java agent that generates heap dumps based on preconfigured conditions in the memory usage of the application. See: [Java Memory Assistant](https://github.com/SAP/java-memory-assistant)

> ### Note:  
> This public repository went out of maintenance on **Sept 21, 2023**. Nevertheless, its latest version [0.5.0](https://github.com/SAP-archive/java-memory-assistant/releases/tag/0.5.0) is working fine so you can keep using it.

To enable the agent in the buildpack, add the following configuration to the `manifest.yml/mtad.yaml` descriptor:

> ### Sample Code:  
> manifest.yml/mtad.yaml
> 
> ```
> ---
> ...
>   env:
>      JBP_CONFIG_JAVA_MEMORY_ASSISTANT: '{enabled : true}'
> ```

When enabled, the agent generates two files – **\*.hprof** \(heap dump\) and **\*.addons**, when the configured memory limits are met.

The **\*.addons** file contains:

-   Command-line parameters

-   Implemented interfaces for the classes

-   Information \(name\) about transient fields for the classes

-   Class and metaspace statistics

-   Stack traces of the last OOM errors


See also: [Java Memory Assistant Framework](https://github.com/cloudfoundry/java-buildpack/blob/main/docs/framework-java_memory_assistant.md) 

