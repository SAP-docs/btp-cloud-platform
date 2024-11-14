<!-- loio588cfd95fbab41178c21ceefd916a311 -->

# Out-Of-Memory Behavior

SAP Java Buildpack prints a histogram of the heap to the logs when the JVM encounters a terminal failure.

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
  - sap_jakarta_buildpack
  env:
    JBP_CONFIG_JAVA_OPTS: 'false, java_opts: ''-XX:+ExitVMOnOutOfMemoryError'''
  ...
```



<a name="loio588cfd95fbab41178c21ceefd916a311__section_xcd_gky_3dc"/>

## Generate Heap Dumps

It's a good practice to generate a **`.hprof`** heap dump file on the event of *OutOfMemoryError* to analyze and find the root cause of the issue.

You can generate heap dumps in two ways:



### Using jvmkill

SAP Java Buildpack allows you to set *jvmkill* agent when staging your application. A *jvmkill* agent is added by default to the properties when starting the Java application process. The following configuration is added:

```
-agentpath:META-INF/.sap_java_buildpack/jvm_kill/jvmkill-<jvmkill_version>.RELEASE-trusty.so=printHeapHistogram=1
```

This is sufficient to print histogram and kill the process by using *jvmkill* once an OOM error occurs. To generate a heap dump, your application should be bound to a volume service named **heap-dump**.

For example, if you have the following parameter specified in the `manifest.yml` file:

```

services:
  - heap-dump
```

it will result in the following set of properties for the *jvmkill* agent:

```
-agentpath:META-INF/.sap_java_buildpack/jvm_kill/jvmkill-<jvmkill_version>-trusty.so=printHeapHistogram=1,heapDumpPath=<heap_dump_volume_path>/<heap_dump_name>.hprof -XX:ErrorFile=<heap_dump_volume_path>/<error_file_name>.log
```

If an OOM error occurs, *jvmkill* will store the heap dump under the relevant volume path.

If you want to disable *jvmkill* and omit its agent being added to the startup properties, use the SJB\_NO\_JVMKILL environment variable, like this:

```

env:
  SJB_NO_JVMKILL: true
```



### Using standard Java properties

Various distributions including *SapMachineJre* and *SapMachineJdk* provide standard mechanism for generating a heap dump in the event of an OOM error. The following properties can be added on startup for this purpose, like this:

```
-XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=<heap_dump_path> -XX:OnOutOfMemoryError='kill -9 %p'
```

**`-XX:+HeapDumpOnOutOfMemoryError`** is sufficient to trigger heap dump generation under a default path. The other two properties specify *where* you want to specify the heapdump file with `-XX:HeapDumpPath`, and *what command or script* you want to be executed if this occurs with `-XX:OnOutOfMemoryError`. The command usually kills the process, as shown in the example in the previous section.

> ### Note:  
> The heap dump is generated and stored in an application container location. This means, it will be removed once the application instance container is restarted. A restart will happen if the process is killed \(like shown in the example in the previous section\).
> 
> Therefore, if you want to dig further in the heap dump file, stored in the application container, the process should not be killed in order to prevent restart.

**Related Information**  


[ActiveProcessorCount](activeprocessorcount-9013611.md "This JVM option overrides the number of CPUs which the virtual machine uses to calculate the size of thread pools for operations (such as garbage collection).")

[Cloud Foundry: jvmkill](https://github.com/cloudfoundry/jvmkill)

