<!-- loioe57288d7f2aa4e59a8f70b08b82a933d -->

# Specify the Location of the Configuration File

You can change the location of the configuration file by using the `--config` option.



## Context

Upon successful login, the btp CLI creates a folder \(`btp`\) and a configuration file \(`config.json`\) in the default location of your user data directory:

-   Microsoft Windows: `C:\Users\*<username\>*\AppData\Local\SAP\btp\config.json`

-   Apple macOS / Linux: `$HOME/.btp/config.json`


This folder serves as the working directory of the btp CLI, that is, it’s necessary for its proper functioning, and is used with each command execution.

If you want the configuration file to be created in a different folder, you can use the `--config` option in your login command and then specify this location in each command call with this `--config` option.



## Procedure

1.  Specify the location of the configuration file with your login command:

    ```
    `btp --config "*<file path\>*" login`
    ```

2.  Specify this location either with the `SAPCP_CLIENTCONFIG` environment variable, or use the `--config` option with each subsequent command call.

    > ### Sample Code:  
    > ```
    > `btp --config "*<file path\>*"`
    > ```




Let's assume you want to work in two subaccounts in parallel, using two terminals. For example, with the first terminal \(A\), you want to work in a subaccount with ID 1000, with the second terminal \(B\) you want to work in a subaccount with ID 2000, and you want to list the users in each subaccount.


<table>
<tr>
<th>

Terminal A



</th>
<th>

Terminal B



</th>
</tr>
<tr>
<td>

1. Log in to your global account using the default location of the configuration file:

```
btp login
```

Run all commands as usual. The btp CLI uses the default configuration file.



</td>
<td>

1. Log in to your global account using a different location of the configuration file:

```
btp --config "C:\my-cli-folder" login
```

Use this option with each command call.



</td>
</tr>
<tr>
<td>

2. Set the default context to subaccount 1000:

```
btp target --subaccount 1000
```



</td>
<td>

2. Set the default context to subaccount 2000:

```
btp --config "C:\my-cli-folder" target --subaccount 2000
```



</td>
</tr>
<tr>
<td>

3. List the users of subaccount 1000:

```
btp list security/user
```



</td>
<td>

3. List the users of subaccount 2000:

```
btp --config "C:\my-cli-folder" list security/user
```



</td>
</tr>
</table>

**Parent topicColonSymbol** [General Commands and Options in the btp CLI](General_Commands_and_Options_in_the_btp_CLI_11d9f67.md "Learn how to work with the SAP BTP command line interface (btp CLI). For example, how to log in, get help, and set a default context for commands.")

**Related Information**  


[Get Help](Get_Help_f8fd1e5.md "Get help in the btp CLI with the --help option.")

[View Version and Current Context](View_Version_and_Current_Context_9c29222.md "To find out the current context you’re working in, run the command btp --info or simply btp.")

[Log in](Log_in_e241b30.md "Log in with the btp CLI is on global account level.")

[Log out](Log_out_9f1c87a.md "Logging out of the configured server removes all user-specific data from the configuration file.")

[Enable Command Autocompletion](Enable_Command_Autocompletion_46355fa.md "Use command autocompletion to save keystrokes when entering command actions, group-object combinations, and their parameters in the SAP BTP command line interface (btp CLI).")

[Set the Default Command Context](Set_the_Default_Command_Context_720645a.md "Change the default context for all command calls to the global account, a directory, or a subaccount by using the btp target command.")

[Change the Output Format to JSON](Change_the_Output_Format_to_JSON_dcb85b7.md "Use the --format json option to change the output format of a command to JSON.")

