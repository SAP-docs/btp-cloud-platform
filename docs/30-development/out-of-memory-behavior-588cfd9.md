<!-- loio588cfd95fbab41178c21ceefd916a311 -->

# Out-Of-Memory Behavior

SAP Java Buildpack prints a histogram of the heap memory to the logs when the JVM encounters a terminal failure.

> ### Output Code:  
> ```
> ERR Stopping VM due to OutOfMemoryError
> ERR Resource exhaustion event: the JVM was unable to allocate memory from the heap.
> ERR ResourceExhausted! (1/0)
> OUT | Instance Count | Total Bytes | Class Name                                    |
> OUT | 30130          | 5556616     | [C                                            |
> OUT | 866            | 2485600     | [B                                            |
> OUT | 29215          | 701160      | Ljava/lang/String;                            |
> OUT | 3971           | 449528      | Ljava/lang/Class;                             |
> OUT | 9998           | 319936      | Ljava/util/HashMap$Node;                      |
> OUT | 3624           | 318912      | Ljava/lang/reflect/Method;                    |
> OUT | 6429           | 205728      | Ljava/util/concurrent/ConcurrentHashMap$Node; |
> OUT | 2821           | 171472      | [Ljava/lang/Object;                           |
> OUT | 40             | 117328      | [J                                            |
> OUT | 750            | 111096      | [Ljava/util/HashMap$Node;                     |
> OUT | 5618           | 89888       | Ljava/lang/Object;                            |
> OUT | 1054           | 74048       | [Ljava/lang/String;                           |
> OUT | 696            | 62552       | [I                                            |
> OUT | 59             | 51920       | [Ljava/util/concurrent/ConcurrentHashMap$Node;|
> OUT | 1063           | 51024       | Ljava/util/HashMap;                           |
> OUT | 854            | 40992       | Lorg/apache/tomcat/util/modeler/AttributeInfo;|
> ...
>  
> 
> ```

This functionality is **activated** by default.

If you want to deactivate it, add property `-XX:+ExitVMOnOutOfMemoryError` through the `JBP_CONFIG_JAVA_OPTS` property in the application's *manifest.yml* file, like this:

```

---
applications:
- name: <APP_NAME>
  buildpacks:
  - sap_java_buildpack_jakarta
  env:
    JBP_CONFIG_JAVA_OPTS: 'false, java_opts: ''-XX:+ExitVMOnOutOfMemoryError'''
  ...
```



<a name="loio588cfd95fbab41178c21ceefd916a311__section_wgj_csw_mdc"/>

## Killing a process with jvmkill

SAP Java Buildpack allows you to set *jvmkill* agent when staging your application. A *jvmkill* agent is added by default to the properties when starting the Java application process. The following configuration is added:

```
-agentpath:META-INF/.sap_java_buildpack/jvm_kill/jvmkill-<jvmkill_version>.RELEASE-trusty.so=printHeapHistogram=1
```

This is sufficient to print a histogram and kill the process when an out-of-memory \(OOM\) error occurs.

If you want to disable *jvmkill* and omit its agent being added to the startup properties, use the SJB\_NO\_JVMKILL environment variable, like this:

```

env:
  SJB_NO_JVMKILL: true
```



## Generate Heap Dumps

It's a good practice to generate an **`.hprof`** heap dump file on the event of *OutOfMemoryError* to analyze and find the root cause of the issue. You can do this the following ways:

-   [Generate with Java Properties](generate-heap-dumps-with-java-properties-63d1e87.md)
-   [Generate with Object Store](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/5a086335e91846bb9a6c0026aecc963d.html "") :arrow_upper_right:

**Related Information**  


[ActiveProcessorCount](activeprocessorcount-9013611.md "This JVM option overrides the number of CPUs which the virtual machine uses to calculate the size of thread pools for operations (such as garbage collection).")

[Cloud Foundry: jvmkill](https://github.com/cloudfoundry/jvmkill)

