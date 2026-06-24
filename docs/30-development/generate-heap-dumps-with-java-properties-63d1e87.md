<!-- loio63d1e8748ce8480a98b4759e4f6da727 -->

# Generate Heap Dumps with Java Properties



## Context

It's a good practice to generate a **`.hprof`** heap dump file on the event of *OutOfMemoryError* to analyze and find the root cause of the issue.

Various distributions including *SapMachineJre* and *SapMachineJdk* provide standard mechanism for generating a heap dump in the event of an OOM error. Proceed as follows:



## Procedure

1.  Add the following properties on startup:

    ```
    -XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=<heap_dump_path> -XX:OnOutOfMemoryError='kill -9 %p'
    ```

    -   **`-XX:+HeapDumpOnOutOfMemoryError`** triggers heap dump generation under a default path.

    -   **`-XX:HeapDumpPath`** specifies *where* to specify the heap dump file.

    -   **`-XX:OnOutOfMemoryError`** specifies *what command or script* to be run if OOM occurs. This command usually kills the process.


    > ### Note:  
    > Killing the process will trigger a restart. Therefore, if you need to investigate further in the heap dump file stored in the application container, the process should not be killed.

2.  The **`.hprof`** heap dump file is generated and stored in an application container location.

    It will be removed once the application instance container is restarted.


