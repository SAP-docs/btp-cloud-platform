<!-- loio97bdeb2e344c4c6380315e19ad4bb483 -->

# Kyma Dashboard Terminal

The Kyma dashboard terminal gives you an interactive shell directly in your browser, without installing any local tools. When you open the terminal, Kyma dashboard creates a lightweight container `Pod` in your cluster and connects your browser to its shell through a WebSocket proxy.



<a name="loio97bdeb2e344c4c6380315e19ad4bb483__section_open_terminal_rcc"/>

## Open the Terminal

To open the terminal, choose the Terminal icon in the top navigation bar. The terminal panel opens at the bottom of the screen.

Kyma dashboard creates the `busola-terminal` namespace in your cluster \(if it does not exist yet\) and starts a `Pod` using the `busola-dev-toolbox` container image.

> ### Caution:  
> When you close the terminal, the `Pod` is deleted. Any tools, files, or configurations you installed or created during the session are lost. The next time you open the terminal, the `Pod` starts fresh.



<a name="loio97bdeb2e344c4c6380315e19ad4bb483__section_available_commands_rcc"/>

## Available Commands

The terminal provides a full interactive Bash shell \(`/bin/bash`\) inside the `busola-dev-toolbox` container. The following are available by default:

-   Standard Linux commands \(`ls`, `cat`, `grep`, `curl`, `wget`, and more\)
-   Additional tools bundled in the [`busola-dev-toolbox` image](https://github.com/kyma-project/busola/blob/main/Dockerfile.dev-toolbox)

> ### Note:  
> `kubectl` is not yet available. The terminal `Pod` runs without a Kubernetes `ServiceAccount`, which means it has no access to the Kubernetes API. The toolset is actively being expanded — future versions will include `kubectl` and Kyma CLI.



<a name="loio97bdeb2e344c4c6380315e19ad4bb483__section_limitations_rcc"/>

## Limitations

The following table summarizes the key limitations of the terminal feature:


<table>
<tr>
<th valign="top">

Limitation

</th>
<th valign="top">

Details

</th>
</tr>
<tr>
<td valign="top">

No `kubectl` access

</td>
<td valign="top">

The terminal `Pod` has no Kubernetes `ServiceAccount`. `kubectl` commands are not available.

</td>
</tr>
<tr>
<td valign="top">

Ephemeral session

</td>
<td valign="top">

Closing the terminal deletes the `Pod`. Files, tools, and settings are not preserved between sessions.

</td>
</tr>
<tr>
<td valign="top">

Single `Pod` per cluster

</td>
<td valign="top">

Each user has one terminal `Pod` per cluster connection.

</td>
</tr>
</table>

**Related Information**  


[Tutorial: Check Services with curl in the Kyma Dashboard Terminal](https://kyma-project.io/external-content/busola/docs/user/tutorials/01-51-terminal-tutorial-curl.html)

