<!-- loioe57288d7f2aa4e59a8f70b08b82a933d -->

# Specify the Location of the Configuration File

You can change the location of the configuration file by using the `--config` option or the environment variable.



## Context

Upon successful login, the btp CLI creates a configuration file \(`config.json`\) in the default location of your user config directory:

-   Microsoft Windows: `C:\Users\*<username\>*\AppData\Roaming\SAP\btp\config.json`

-   Apple macOS ; `~/Library/Application Support/.btp/config.json`

-   Linux: `~/.config/.btp/config.json`


This folder serves as the working directory of the btp CLI, that is, it’s necessary for its proper functioning, and is used with each command execution.

If you want the configuration file to be created in a different folder, you can use the `--config` option in your login command and then specify this location in each command call with this `--config` option.



## Procedure

1.  Specify the location of the configuration file with your login command:

    ```
    `btp --config "*<file path\>*" login`
    ```

2.  Specify this location either with the `BTP_CLIENTCONFIG` environment variable, or use the `--config` option with each subsequent command call.

    > ### Sample Code:  
    > ```
    > `btp --config "*<file path\>*"`
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

2. Set the default context to subaccount 1000:

```
btp target --subaccount 1000
```



</td>
<td valign="top">

2. Set the default context to subaccount 2000:

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

**Related Information**  


[Get Help](get-help-f8fd1e5.md "There is extensive help in the btp CLI about every command. You can get help with the help action or the --help option.")

[View Version and Current Context](view-version-and-current-context-9c29222.md "To find out the current context you’re working in, run the command btp --info or simply btp.")

[Log in](log-in-e241b30.md "Log in with the btp CLI is on global account level.")

[Log out](log-out-9f1c87a.md "Logging out of the configured server removes all user-specific data from the configuration file.")

[Enable Command Autocompletion](enable-command-autocompletion-46355fa.md "Use command autocompletion to save keystrokes when entering command actions, group-object combinations, and their parameters in the SAP BTP command line interface (btp CLI).")

[Set the Default Command Context](set-the-default-command-context-720645a.md "Change the default context for all command calls to the global account, a directory, or a subaccount by using the btp target command.")

[Change the Output Format to JSON](change-the-output-format-to-json-dcb85b7.md "Use the --format json option to change the output format of a command to JSON.")

