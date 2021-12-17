<!-- loio720645a3ed3945bd8d97a670b948ac07 -->

# Set the Default Command Context

Change the default context for all command calls to the global account, a directory, or a subaccount by using the `btp target` command.



## Context

If you know you need to work in one particular subaccount or directory, you can change the default context for command execution, so you won't have to enter that subaccount's or directory's ID with every command call. Targeting works along the hierarchy of your account model:

-   After login, the global account is targeted by default.

-   Commands that only work on a directory or global account level will be executed in the parent directory or global account of the current target.

-   When targeting a subaccount or directory, you can execute commands in its parent directory or global account by using '-dir' or '-ga' without a value.




## Procedure

1.  Use `btp target [PARAMS]` to set the context for subsequent commands.

    Usage: `btp [OPTIONS] target [PARAMS]`

    <a name="loio720645a3ed3945bd8d97a670b948ac07__table_ovd_5ms_w3b"/>Parameters


    <table>
    <tr>
    <td valign="top">

    `--global-account, -ga` *<SUBDOMAIN\>*


    
    </td>
    <td valign="top">

    Only the global account of the active login can be targeted. As only one active login is possible, SUBDOMAIN can be omitted.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    `--directory, -dir`*<ID\>*


    
    </td>
    <td valign="top">

    The ID of the directory to be targeted. You can find the directory ID by running `btp get accounts/global-account --show-hierarchy`


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    `--subaccount, -sa` *<ID\>*


    
    </td>
    <td valign="top">

    The ID of the subaccount to be targeted. You can find this ID by running `btp list accounts/subaccount`.


    
    </td>
    </tr>
    </table>
    



<a name="loio720645a3ed3945bd8d97a670b948ac07__result_f5r_jms_w3b"/>

## Results

Once you have set the context to a subaccount, all subsequent commands are executed there, unless you specify a different one by providing one of the parameters directly in a command call.

> ### Tip:  
> To find out your current context, use `btp --info` or simply `btp`.



To set the context back to the global account, use `btp target -ga`.

**Related Information**  


[Get Help](get-help-f8fd1e5.md "There is extensive help in the btp CLI about every command. You can get help with the help action or the --help option.")

[View Version and Current Context](view-version-and-current-context-9c29222.md "To find out the current context you’re working in, run the command btp --info or simply btp.")

[Log in](log-in-e241b30.md "Log in with the btp CLI is on global account level.")

[Log out](log-out-9f1c87a.md "Logging out of the configured server removes all user-specific data from the configuration file.")

[Enable Command Autocompletion](enable-command-autocompletion-46355fa.md "Use command autocompletion to save keystrokes when entering command actions, group-object combinations, and their parameters in the SAP BTP command line interface (btp CLI).")

[Change the Output Format to JSON](change-the-output-format-to-json-dcb85b7.md "Use the --format json option to change the output format of a command to JSON.")

[Specify the Location of the Configuration File](specify-the-location-of-the-configuration-file-e57288d.md "You can change the location of the configuration file by using the --config option or the environment variable.")

[Commands in the btp CLI](commands-in-the-btp-cli-a03a555.md "A list of all tasks and respective commands that are available in the SAP BTP command line interface (btp CLI).")

[Global Accounts](../10-concepts/account-model-8ed4a70.md#loioc165d95ee700407eb181770901caec94 "A global account is the realization of a contract you made with SAP.")

