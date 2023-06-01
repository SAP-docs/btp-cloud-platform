<!-- loioe57288d7f2aa4e59a8f70b08b82a933d -->

# Specify the Location of the Configuration File

You can change the location of the configuration file by using the `--config` option or the environment variable.



## Context

Upon successful login, the btp CLI creates a configuration file \(`config.json`\) in the default location of your user config directory:

-   Microsoft Windows: <code>C:\Users\<i class="varname">&lt;username&gt;</i>\AppData\Roaming\SAP\btp\config.json</code>

-   Apple macOS ; `~/Library/Application Support/.btp/config.json`

-   Linux: `~/.config/.btp/config.json`


This folder serves as the working directory of the btp CLI, that is, it’s necessary for its proper functioning, and is used with each command execution.

If you want the configuration file to be created in a different folder, you can use the `--config` option in your login command and then specify this location in each command call with this `--config` option.



## Procedure

1.  Specify the location of the configuration file with your login command:

    ```
    btp --config "<file path>" login
    ```

2.  Specify this location either with the `BTP_CLIENTCONFIG` environment variable, or use the `--config` option with each subsequent command call.

    > ### Sample Code:  
    > ```
    > btp --config "<file path>"
    > ```

    > ### Note:  
    > In version 2.14, the environment variable `BTP_CLIENTCONFIG` was introduced. If you use an older client version, you need to use `SAPCP_CLIENTCONFIG`. Although the old one is kept, we recommend to switch to `BTP_CLIENTCONFIG`.




Let's assume you want to work in two subaccounts in parallel, using two terminals. For example, with the first terminal \(A\), you want to work in a subaccount with ID 1000, with the second terminal \(B\) you want to work in a subaccount with ID 2000, and you want to list the users in each subaccount.


<table>
<tr>
<th valign="top">

Terminal A



</th>
<th valign="top">

Terminal B



</th>
</tr>
<tr>
<td valign="top">

1. Log in to your global account using the default location of the configuration file:

```
btp login
```

Run all commands as usual. The btp CLI uses the default configuration file.



</td>
<td valign="top">

1. Log in to your global account using a different location of the configuration file:

```
btp --config "C:\my-cli-folder" login
```

Use this option with each command call.



</td>
</tr>
<tr>
<td valign="top">

2. Set the target to subaccount 1000:

```
btp target --subaccount 1000
```



</td>
<td valign="top">

2. Set the target to subaccount 2000:

```
btp --config "C:\my-cli-folder" target --subaccount 2000
```



</td>
</tr>
<tr>
<td valign="top">

3. List the users of subaccount 1000:

```
btp list security/user
```



</td>
<td valign="top">

3. List the users of subaccount 2000:

```
btp --config "C:\my-cli-folder" list security/user
```



</td>
</tr>
</table>

