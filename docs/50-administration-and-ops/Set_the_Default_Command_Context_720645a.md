<!-- loio720645a3ed3945bd8d97a670b948ac07 -->

# Set the Default Command Context

Change the default context for all command calls to the global account, a directory, or a subaccount by using the `btp target` command.



## Context

Targeting works along the hierarchy of your account model:

-   After login, the global account is targeted by default.

-   Commands that only work on a directory or global account level will be executed in the parent directory or global account of the current target.

-   When targeting a subaccount or directory, you can execute commands in its parent directory or global account by using '-dir' or '-ga' without a value.




## Procedure

1.  Use `btp target [PARAMS]` to set the context for subsequent commands.

    Usage: `btp [OPTIONS] target [PARAMS]`

    <a name="loio720645a3ed3945bd8d97a670b948ac07__table_ovd_5ms_w3b"/>Parameters


    <table>
    <tr>
    <td>

    `--global-account, -ga` *<SUBDOMAIN\>*


    
    </td>
    <td>

    Only the global account of the active login can be targeted. As only one active login is possible, SUBDOMAIN can be omitted.


    
    </td>
    </tr>
    <tr>
    <td>

    `--directory, -dir`*<ID\>*


    
    </td>
    <td>

    The ID of the directory to be targeted. You can find the directory ID by running `btp get accounts/global-account --show-hierarchy`


    
    </td>
    </tr>
    <tr>
    <td>

    `--subaccount, -sa` *<ID\>*


    
    </td>
    <td>

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

**Parent topicColonSymbol** [General Commands and Options in the btp CLI](General_Commands_and_Options_in_the_btp_CLI_11d9f67.md "Learn how to work with the SAP BTP command line interface (btp CLI). For example, how to log in, get help, and set a default context for commands.")

**Related Information**  


[Get Help](Get_Help_f8fd1e5.md "Get help in the btp CLI with the --help option.")

[View Version and Current Context](View_Version_and_Current_Context_9c29222.md "To find out the current context you’re working in, run the command btp --info or simply btp.")

[Log in](Log_in_e241b30.md "Log in with the btp CLI is on global account level.")

[Log out](Log_out_9f1c87a.md "Logging out of the configured server removes all user-specific data from the configuration file.")

[Enable Command Autocompletion](Enable_Command_Autocompletion_46355fa.md "Use command autocompletion to save keystrokes when entering command actions, group-object combinations, and their parameters in the SAP BTP command line interface (btp CLI).")

[Change the Output Format to JSON](Change_the_Output_Format_to_JSON_dcb85b7.md "Use the --format json option to change the output format of a command to JSON.")

[Specify the Location of the Configuration File](Specify_the_Location_of_the_Configuration_File_e57288d.md "You can change the location of the configuration file by using the --config option.")

[Commands in the btp CLI](Commands_in_the_btp_CLI_a03a555.md "A list of all tasks and respective commands that are available in the SAP BTP command line interface (btp CLI).")

[Global Accounts](../10-concepts/Account_Model_8ed4a70.md#loioc165d95ee700407eb181770901caec94 "A global account is the realization of a contract you made with SAP.")

