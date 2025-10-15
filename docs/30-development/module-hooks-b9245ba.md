<!-- loiob9245ba90aa14681a416065df8e8c593 -->

# Module Hooks

Define and execute hooks at specific phases of module deployment.

> ### Note:  
> The module hooks are supported from major schema version 3 onwards. If they are specified but schema version is below 3, they are ignored.

You can use hooks to change the typical deployment process, in this case to enable tasks to be executed during a specific moment of the application deployment. For example, you can set hooks to be executed before or after the actual deployment steps for a module, depending on the applications' need.

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

In the example above, the hook attributes are:

-   `name` – defines the name of the hook.
-   `type` – defines the type of the hook. Currently, the only supported type is `task`.
-   `phases` – defines the specific moment when a hook is executed. The `phases` element denotes that the hook is executed before the application is stopped. The suffixes `live` and `idle` are used during blue-green deployments and indicate when the `before-stop` phase is executed.

    > ### Example:  
    > In the example above, the `blue-green.application.before-stop.idle` phase executes the hook when the new idle applications are redirected to the new live routes, and the `blue-green.application.before-stop.live` is used just before the deletion of the live application.

-   `parameters` – defines the parameters of the hook. For the hooks of type `task`, the parameters must define a one-off task.

Depending on the deployment strategy you use, the `phases` values are:

-   **For regular deployment**


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
    
    `blue-green.application.before-stop.idle` 
    
    </td>
    <td valign="top">
    
    `task`
    
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
    
    Executed before the live application corresponding to the module is started.
    
    </td>
    </tr>
    </table>
    



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

