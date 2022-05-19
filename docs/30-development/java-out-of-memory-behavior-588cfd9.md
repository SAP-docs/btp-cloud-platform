<!-- loio588cfd95fbab41178c21ceefd916a311 -->

# Java Out Of Memory Behavior

The SAP Java Buildpack prints a histogram of the heap to the logs, when the JVM encounters a terminal failure. In addition to that, if the application is bound to a volume service with name or tag that contains *heap-dump*, a heap dump file is also generated and stored in the mounted volume.

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

This functionality is activated by default. It is possible to deactivate it by adding the `-XX:+ExitVMOnOutOfMemoryError` property \(through the `JBP_CONFIG_JAVA_OPTS` property\) in the application manifest file.

> ### Sample Code:  
> ```
> JBP_CONFIG_JAVA_OPTS: 'false, java_opts: ''-XX:+ExitVMOnOutOfMemoryError'''
> ```

For more information about the *jmvkill* agent, see [Cloud Foundry jvmkill documentation](https://github.com/cloudfoundry/jvmkill).

