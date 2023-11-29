<!-- loioa1c184c585f24c1c8dfaf4d1fcc2fde7 -->

# Tasks

Create one-off administration tasks or scripts.

During the deployment process, these tasks can be executed against staged applications. The platform creates a new container for them, where they are performed for a specific period until they are completed, after which the container is deleted.

One-off tasks are modeled in accordance to the following structure:

> ### Sample Code:  
> ```
> _schema-version: "3.1"
> ID: foo
> version: 3.0.0
> modules:
>   - name: foo
>     type: javascript.nodejs
>     parameters:
>       no-route: true
>       no-start: true
>       disk-quota: 2GB
>       tasks:
>       - name: example_task
>         command: npm start
>         memory: 1GB
>        
> ```

In the structure above, the parameters stand for the following:

-   When the task is triggered, the `npm start` command is executed.
-   Entering a specific value in the `memory` parameter is optional. A platform-derived default memory size is used for the execution of the task. You can specify a different value if required.
-   The `no-route` parameter specifies if a route is required. Applications whose only purpose is to perform a task and then be stopped usually do not require a route. The default value is `false`.
-   Use the `no-start` parameter if you want only the one-off tasks to be executed, that is, without triggering the start of the application. If you do not define this parameter, tasks are automatically executed after the applications are started.

> ### Note:  
> Тhe values for аpplication memory and task memory do not have a dependency. This is also valid for the allowed disk quota.

> ### Tip:  
> For more information about one-off tasks, see [MTA Deployment Descriptor Examples](mta-deployment-descriptor-examples-66a7033.md).

The following codeblock contains an example for a database migration task:

> ### Sample Code:  
> ```
> _schema-version: "3.1"
> ID: foo
> version: 3.0.0
> modules:
>   - name: foo
>     type: javascript.nodejs
>     parameters:
>       no-route: true
>       no-start: true
>       memory: 1GB
>       disk-quota: 2GB
>       tasks:
>         - name: db_migration
>           command: "bin/rails db:migrate"
>           memory: 256M                    #This parameter is optional.
>           disk-quota: 128M                #This parameter is optional.
> 
> 
> ```

**Related Information**  


[Using Tasks](https://docs.cloudfoundry.org/devguide/using-tasks.html)

