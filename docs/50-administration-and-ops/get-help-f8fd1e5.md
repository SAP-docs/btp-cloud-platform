<!-- loiof8fd1e5bbf9649e1936d32fb9614677b -->

# Get Help

There is extensive help in the btp CLI about every command. You can get help with the `help` action or the `--help` option.

There are several ways to call help in the btp CLI, and there is help on all levels, from a basic entry page thats explains the syntax to very detailed command-specific help that explains the usage of a command and its parameters in detail.

The easiest way to get help is probably the `help` action \(for basic help, use `btp help`, as shown in the examples below. But you can also place `--help` at the end or beginning of a command call, for example, `btp list help`, `btp --help list`, and `btp list --help` are interchangeable.

Here's the help syntax:

-   `btp help`

-   `btp help <ACTION>`

-   `btp help <GROUP>`

-   `btp help <GROUP>/<OBJECT>`



<table>
<tr>
<th valign="top">

Example Help Calls \(progressing in level of detail\)



</th>
<th valign="top">

What to Expect



</th>
</tr>
<tr>
<td valign="top">

`btp help`



</td>
<td valign="top">

Explains the syntax and shows plenty of examples.



</td>
</tr>
<tr>
<td valign="top">

`btp help all`



</td>
<td valign="top">

Displays an overview of all available commands, ordered according to their group/object combinations.



</td>
</tr>
<tr>
<td valign="top">

`btp help list`



</td>
<td valign="top">

Displays *list* commands with short summaries.



</td>
</tr>
<tr>
<td valign="top">

`btp help accounts`



</td>
<td valign="top">

Displays all objects in *accounts* group, and all available actions per group/object combination.



</td>
</tr>
<tr>
<td valign="top">

`btp help accounts/subaccount`



</td>
<td valign="top">

Displays all available commands for this group/object combination.



</td>
</tr>
<tr>
<td valign="top">

`btp help list accounts/subaccount`



</td>
<td valign="top">

Displays command-specific help, such as usage, a list of all parameters with descriptions, helpful tips, examples, and links to further documentation.



</td>
</tr>
</table>

**Related Information**  


[View Version and Current Context](view-version-and-current-context-9c29222.md "To find out the current context you’re working in, run the command btp --info or simply btp.")

[Log in](log-in-e241b30.md "Log in with the btp CLI is on global account level.")

[Log out](log-out-9f1c87a.md "Logging out of the configured server removes all user-specific data from the configuration file.")

[Enable Command Autocompletion](enable-command-autocompletion-46355fa.md "Use command autocompletion to save keystrokes when entering command actions, group-object combinations, and their parameters in the SAP BTP command line interface (btp CLI).")

[Set a Target for Subsequent Commands with btp target](set-a-target-for-subsequent-commands-with-btp-target-720645a.md "Change the target for command calls to a directory, a subaccount, or the global account, by using the btp target command.")

[Change the Output Format to JSON](change-the-output-format-to-json-dcb85b7.md "Use the --format json option to change the output format of a command to JSON.")

[Specify the Location of the Configuration File](specify-the-location-of-the-configuration-file-e57288d.md "You can change the location of the configuration file by using the --config option or the environment variable.")

[Command Syntax of the btp CLI](command-syntax-of-the-btp-cli-69606f4.md "Each command consists of the base call btp followed by a verb (the action), a combination of group and object, and parameters.")

