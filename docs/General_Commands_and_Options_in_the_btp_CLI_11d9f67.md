<!-- loio11d9f67d2c68485ca2f435b955d3b85b -->

# General Commands and Options in the btp CLI

Learn how to work with the SAP BTP command line interface \(btp CLI\). For example, how to log in, get help, and set a default context for commands.



<a name="loio11d9f67d2c68485ca2f435b955d3b85b__section_dw1_wg3_xkb"/>

## General Commands

```
`btp login`
```

```
`btp logout`
```

```
`btp target`
```



<a name="loio11d9f67d2c68485ca2f435b955d3b85b__section_pdm_xg3_xkb"/>

## General Options for Each Command

The following options are available for each command. They need to be typed right after the base call `btp`, and they can be combined \(for example, `btp --verbose --help list accounts/subaccount`. The `--help` option also works at the end of a command call.


<table>
<tr>
<th>

Options



</th>
<th>

 



</th>
</tr>
<tr>
<td>

--config



</td>
<td>

Specifies the location of the configuration file. See [Specify the Location of the Configuration File](Specify_the_Location_of_the_Configuration_File_e57288d.md).



</td>
</tr>
<tr>
<td>

--info



</td>
<td>

Displays version and current context. Note that this option only works on its own \(`btp --info)` and cannot be added to other command calls. You can also just use `btp` to display the info. See [View Version and Current Context](View_Version_and_Current_Context_9c29222.md).



</td>
</tr>
<tr>
<td>

--help



</td>
<td>

Displays help. See [Get Help](Get_Help_f8fd1e5.md).



</td>
</tr>
<tr>
<td>

--verbose



</td>
<td>

Prints tracing information for support. See [Troubleshooting and Support](Troubleshooting_and_Support_4023e15.md).



</td>
</tr>
<tr>
<td>

--format



</td>
<td>

Changes the output format of a command to JSON. See [Change the Output Format to JSON](Change_the_Output_Format_to_JSON_dcb85b7.md).



</td>
</tr>
</table>

-   **[Get Help](Get_Help_f8fd1e5.md "Get help in the btp CLI with the --help option.")**  
Get help in the btp CLI with the `--help` option.
-   **[View Version and Current Context](View_Version_and_Current_Context_9c29222.md "To find out the current context you’re working in, run the command btp --info or simply
		btp.")**  
To find out the current context you’re working in, run the command `btp --info` or simply `btp`.
-   **[Log in](Log_in_e241b30.md "Log in with the btp CLI is on global account level.")**  
Log in with the btp CLI is on global account level.
-   **[Log out](Log_out_9f1c87a.md "Logging out of the configured server removes all user-specific data from the configuration file.")**  
Logging out of the configured server removes all user-specific data from the configuration file.
-   **[Enable Command Autocompletion](Enable_Command_Autocompletion_46355fa.md "Use command autocompletion to save keystrokes when entering command actions, group-object combinations, and their parameters in the SAP BTP command line interface (btp CLI).")**  
Use command autocompletion to save keystrokes when entering command actions, group-object combinations, and their parameters in the SAP BTP command line interface \(btp CLI\).
-   **[Set the Default Command Context](Set_the_Default_Command_Context_720645a.md "Change the default context for all command calls to the global account, a directory, or a subaccount by using the btp
			target command.")**  
Change the default context for all command calls to the global account, a directory, or a subaccount by using the `btp target` command.
-   **[Change the Output Format to JSON](Change_the_Output_Format_to_JSON_dcb85b7.md "Use the --format json option to change the output format of a command to JSON.")**  
Use the `--format json` option to change the output format of a command to JSON.
-   **[Specify the Location of the Configuration File](Specify_the_Location_of_the_Configuration_File_e57288d.md "You can change the location of the configuration file by using the --config option.")**  
You can change the location of the configuration file by using the `--config` option.

**Related Information**  


[Commands in the btp CLI](Commands_in_the_btp_CLI_a03a555.md "A list of all tasks and respective commands that are available in the SAP BTP command line interface (btp CLI).")

