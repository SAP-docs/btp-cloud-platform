<!-- loiob9245ba90aa14681a416065df8e8c593 -->

# Module Hooks

Define and execute hooks at specific phases of module deployment.

> ### Note:  
> The module hooks are supported from major schema version 3 onwards. If they are specified but schema version is below 3, they are ignored.

You can use hooks to change the typical deployment process, in this case to enable tasks to be executed during a specific moment of the application deployment. For example, you can set hooks to be executed before or after the actual deployment steps for a module, depending on the applications' needs.

> ### Note:  
> Currently, module hooks are only Cloud Foundry app tasks. Therefore, the timeout of a hook is the task execution timeout defined for the respective module. For more information, see [Application-Specific Timeouts](applications-0540211.md#loio05402110821742479725338cc8d7fe8c__section_qlj_kky_ncc).

When added to the deployment descriptor, module hooks are modeled as follows:

> ### Sample Code:  
> ```
> _schema-version: "3.3"
> ID: foo
> version: 3.0.0
> modules:
>   - name: foo
>     type: javascript.nodejs
>     hooks:
>       - name: hook
>         type: task
>         phases:
>           - blue-green.application.before-stop.live
>           - blue-green.application.before-stop.idle
>         parameters:
>           name: foo-task
>           command: 'sleep 5m'
> ```

A module hook is defined with the following attributes:

-   `name` – defines the name of the hook.
-   `type` – defines the type of the hook. Currently, the only supported type is `task`.
-   `phases` – defines the specific moment when a hook is executed. In the example above, the `phases` element denotes that the hook is executed before the application is stopped. The suffixes `live` and `idle` are used during blue-green deployments and indicate when the `before-stop` phase is executed.

    > ### Example:  
    > In the example above, the `blue-green.application.before-stop.idle` phase executes the hook when the new idle applications are redirected to the new live routes, and the `blue-green.application.before-stop.live` is used just before the deletion of the live application.

-   `parameters` – defines the parameters of the hook. For the hooks of type `task`, the parameters must define a one-off task. See [Module Hooks - Specific Parameters](module-hooks-b9245ba.md#loiob9245ba90aa14681a416065df8e8c593__section_byz_kcf_wjb).



## Deployment Phases

Deployment hook phases are specific to the deployment strategy. Phases defined for a standard deployment are only executed during a standard deployment, while phases defined for a blue-green deployment are only executed during a blue-green deployment. Phases that do not match the deployment type are ignored.

Depending on the deployment strategy you use, the `phases` values are:

-   **For standard deployment**


    <table>
    <tr>
    <th valign="top">

    Phase
    
    </th>
    <th valign="top">

    Supported for types
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `deploy.application.before-stop`
    
    </td>
    <td valign="top">
    
    `task`
    
    </td>
    <td valign="top">
    
    Executed before the application corresponding to the module is stopped.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `deploy.application.after-stop`
    
    </td>
    <td valign="top">
    
    `task`
    
    </td>
    <td valign="top">
    
    Executed after the application corresponding to the module is stopped.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `deploy.application.before-start`
    
    </td>
    <td valign="top">
    
    `task`
    
    </td>
    <td valign="top">
    
    Executed before the application corresponding to the module is started.
    
    </td>
    </tr>
    </table>
    
-   **For blue-green deployment**

    In a blue-green deployment context, **live** refers to the previously deployed application version, while **idle** refers to the newly deployed application version. For more information, see [Blue-Green Deployment of Multitarget Applications](blue-green-deployment-of-multitarget-applications-772ab72.md).

    The **Default Target App** column shows the application on which the hook task is executed by default. The override the target application for a specific phase, see [Overriding the Default Target App for Hook Execution](module-hooks-b9245ba.md#loiob9245ba90aa14681a416065df8e8c593__override-target-app).


    <table>
    <tr>
    <th valign="top">

    Phase
    
    </th>
    <th valign="top">

    Supported for types
    
    </th>
    <th valign="top">

    Default Target App
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `blue-green.application.before-stop.idle` 
    
    </td>
    <td valign="top">
    
    `task`
    
    </td>
    <td valign="top">
    
    idle
    
    </td>
    <td valign="top">
    
    Executed before the idle application corresponding to the module is stopped. Idle applications are created as part of blue-green deployments and are restarted \(stopped and started again\) after the deployment validation phase of their productization. That is after the live routes are mapped to them and their environments are rebuilt to contain only live routes.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `blue-green.application.before-stop.live`
    
    </td>
    <td valign="top">
    
    `task`
    
    </td>
    <td valign="top">
    
    live
    
    </td>
    <td valign="top">
    
    Executed before the live application corresponding to the module is stopped. Live applications are the ones that are already up and running before the deployment starts.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `blue-green.application.after-stop.idle`
    
    </td>
    <td valign="top">
    
    `task`
    
    </td>
    <td valign="top">
    
    idle
    
    </td>
    <td valign="top">
    
    Executed after the idle application corresponding to the module is stopped.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `blue-green.application.after-stop.live`
    
    </td>
    <td valign="top">
    
    `task`
    
    </td>
    <td valign="top">
    
    live
    
    </td>
    <td valign="top">
    
    Executed after the live application corresponding to the module is stopped.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `blue-green.application.before-unmap-routes.live`
    
    </td>
    <td valign="top">
    
    `task`
    
    </td>
    <td valign="top">
    
    live
    
    </td>
    <td valign="top">
    
    Executed before unmapping the route of the live application that corresponds to the module.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `blue-green.application.before-start.idle`
    
    </td>
    <td valign="top">
    
    `task`
    
    </td>
    <td valign="top">
    
    idle
    
    </td>
    <td valign="top">
    
    Executed before the idle application corresponding to the module is started.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `blue-green.application.before-start.live`
    
    </td>
    <td valign="top">
    
    `task`
    
    </td>
    <td valign="top">
    
    idle
    
    </td>
    <td valign="top">
    
    Executed before the live application corresponding to the module is started.

    > ### Note:  
    > Although this phase name carries the `.live` suffix, the task runs on the idle application by default, because at this point of the deployment it is the idle application that is being restarted with its live route configuration as part of being promoted to the live role.


    
    </td>
    </tr>
    </table>
    



<a name="loiob9245ba90aa14681a416065df8e8c593__override-target-app"/>

## Overriding the Default Target App for Hook Execution

By default, each blue-green deployment phase executes its hook task on the application that corresponds to the phase suffix. Phases with the `.live` suffix run on the live application, and phases with the `.idle` suffix run on the idle application. The exception is `blue-green.application.before-start.live`, which runs on the idle application by default \(see the table above for more information\).

You can use the `phases-config` parameter to override the default target application for one or more phases within a single hook definition. This makes it possible to define whether a hook should be executed on the live or idle application for a specific phase.

> ### Example:  
> In the following example, the hook is triggered during the `blue-green.application.after-stop.live` phase, but the task is executed on the idle application instead of the default live application:
> 
> ```
> hooks: 
>   - name: target-app-test 
>     type: task 
>     phases: 
>       - blue-green.application.after-stop.live 
>     parameters: 
>       command: "echo Executing hook" 
>       phases-config: 
>         - phase: blue-green.application.after-stop.live
>           target-app: idle
> ```
> 
> You can also configure this for multiple phases at once:
> 
> ```
> hooks:
>   - name: target-app-test
>     type: task
>     phases:
>       - blue-green.application.after-stop.live
>       - blue-green.application.before-start.idle
>     parameters:
>       command: "echo Executing hook"
>       phases-config:
>         - phase: blue-green.application.after-stop.live
>           target-app: idle
>         - phase: blue-green.application.before-start.idle
>           target-app: live
> ```

Phases listed in the hook's `phases` array but not referenced in `phases-config` continue to run on their default target application.

> ### Note:  
> Only one `target-app` entry can be defined per phase. Multiple entries for the same phase are not supported.



<a name="loiob9245ba90aa14681a416065df8e8c593__section_byz_kcf_wjb"/>

## Module Hooks - Specific Parameters

The table below contains the parameters of the supported module hook types:

**Module-Hooks-Specific Parameters**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Scope

</th>
<th valign="top">

Read-Only / Write

</th>
<th valign="top">

Description

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Example

</th>
</tr>
<tr>
<td valign="top">

`name` 

</td>
<td valign="top">

Module Hook

</td>
<td valign="top">

Write

</td>
<td valign="top">

Defines the name of the Cloud Foundry task that should be executed

</td>
<td valign="top">

The name of the hook

</td>
<td valign="top">

`name: db_migration`

</td>
</tr>
<tr>
<td valign="top">

`command`

> ### Note:  
> This is a mandatory parameter.



</td>
<td valign="top">

Module Hook

</td>
<td valign="top">

Write

</td>
<td valign="top">

Defines the actual command that is executed as a Cloud Foundry task

</td>
<td valign="top">

 

</td>
<td valign="top">

`command: "bin/rails db:migrate"` 

</td>
</tr>
<tr>
<td valign="top">

`memory` 

</td>
<td valign="top">

Module Hook

</td>
<td valign="top">

Write

</td>
<td valign="top">

Defines the memory that is available to the Cloud Foundry task

</td>
<td valign="top">

Landscape-specific value that is equal to the default application memory

> ### Remember:  
> Do not rely on the default value, as it will probably be much higher than you need and may not fit into the limitations of your quota.



</td>
<td valign="top">

`memory: 256M`

`memory: 1G`

</td>
</tr>
<tr>
<td valign="top">

`disk-quota` 

</td>
<td valign="top">

Module Hook

</td>
<td valign="top">

Write

</td>
<td valign="top">

Defines the disk space that is available to the Cloud Foundry task

</td>
<td valign="top">

Landscape-specific value that is equal to the default application disk quota

> ### Remember:  
> Do not rely on the default value, as it will probably be much higher than you need and may not fit into the limitations of your quota.



</td>
<td valign="top">

`disk-quota: 256M`

`disk-quota: 1G`

</td>
</tr>
<tr>
<td valign="top">

`phases-config` 

</td>
<td valign="top">

Module Hook

</td>
<td valign="top">

Write

</td>
<td valign="top">

Overrides the default target application \(`live` or `idle`\) on which a hook task is executed for a specific blue-green deployment phase. Valid values for `target-app` are `live` and `idle`. For more information, see [Overriding the Default Target App for Hook Execution](module-hooks-b9245ba.md#loiob9245ba90aa14681a416065df8e8c593__override-target-app).

</td>
<td valign="top">

 

</td>
<td valign="top">

```
phases-config: 
  - phase: blue-green.application.after-stop.live
    target-app: idle
```

This hook will be executed on the idle application, after the stop of the live application.

</td>
</tr>
</table>



<a name="loiob9245ba90aa14681a416065df8e8c593__section_vtx_qcf_wjb"/>

## Extending Module Hooks Through an Extension Descriptor

You can also extend module hooks through the extension descriptor. To do so, add the code with your specific parameters, similarly to the following example:

> ### Sample Code:  
> ```
> _schema-version: "3.3"
> ID: foo-change-command
> extends: foo
> 
> modules:
>   - name: foo
>     hooks:
>       - name: hook
>         parameters:
>           command: 'sleep 1m'
> 
> ```

**Related Information**  


[MTA Deployment Descriptor Examples](mta-deployment-descriptor-examples-66a7033.md "Examples of MTA deployment descriptors.")

[Defining Multitarget Application Deployment Descriptors for Cloud Foundry](defining-multitarget-application-deployment-descriptors-for-cloud-foundry-f48880b.md)

[Defining MTA Extension Descriptors](defining-mta-extension-descriptors-50df803.md)

[Legacy Blue-Green Deployment](legacy-blue-green-deployment-764308c.md "Use the legacy blue-green deployment strategy of multitarget applications.")

