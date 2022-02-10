<!-- loio720645a3ed3945bd8d97a670b948ac07 -->

# Set a Target for Subsequent Commands with `btp target`

Set the target for command calls to a subaccount, a directory, or the global account with the `btp target` command.



## Context

After login, the global account is targeted by default. This means that commands are executed in the global account unless you specify otherwise via a parameter. If you know that you need to work in a particular subaccount or directory, you can change the target, so that you won't have to specify that subaccount's or directory's ID as a parameter with every command call. Note that by setting the target to a subaccount or directory, you also target its parent entities. This means that the btp CLI will try to execute the command in the targeted entity first, and, if the command is not available on that level, it will try on the next level, until it reaches the global account. This can be useful, for example, if you have targeted a subaccount, but want to update its parent directory. You can then execute `btp update accounts/directory` without specifying the directory ID.

To see the current target, use `btp --info` or simply `btp`.

To explicitly execute a command in a parent entity instead of in the target, you can specify this with '-dir' or '-ga' parameters without a value. The value is then taken from the target hierarchy. This can be useful, for example, if you have targeted a subaccount, but want to list the users of the parent directory. You can then execute `btp list security/user -dir`. Note, however, that this command is only available on a directory level if the directory is enabled to manage authorizations.



## Procedure

1.  Use `btp target [PARAMS]` to set the target for subsequent commands. Specify one of the following parameters:

    Usage: `btp [OPTIONS] target [PARAMS]`


    <table>
    <tr>
    <th valign="top">

    Parameter


    
    </th>
    <th valign="top">

    Description


    
    </th>
    </tr>
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

    The ID of the directory to be targeted. You can find the directory ID by using `btp get accounts/global-account --show-hierarchy`.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    `--subaccount, -sa` *<ID\>*


    
    </td>
    <td valign="top">

    The ID of the subaccount to be targeted. You can find the subaccount ID by using `btp list accounts/subaccount`.


    
    </td>
    </tr>
    </table>
    



<a name="loio720645a3ed3945bd8d97a670b948ac07__result_f5r_jms_w3b"/>

## Results

The CLI client displays the targeted account entity in its account hierarchy. To execute a command in the targeted entity, you can omit this parameter.



A global account can group together different directories and subaccounts that the global account administrator makes available to users. CLI commands can be executed on all levels of this account hierarchy, that is in the global account, a directory, or a subaccount, usually specified by the above-mentioned parameters. The table below shows some example commands, and explains in which account entity they can be executed and how the target mechanism can be used.

Let's look at a global account that contains a directory with a targeted subaccount. With `btp`, the current target hierarchy is displayed like this:

```nocode
Current target hierarchy:
  Global account (subdomain: cee12xx1trial-ga)
  └─ Directory (ID: 371eXXXX-55XX-40XX-b3XX-e9947ed9XXXX)
     └─ Subaccount (ID: d8aeXXXX-74XX-49XX-89XX-f058029eXXXX)

```

Now, when you run commands without specifying an account entity as parameter, they are executed in the targeted subaccount or in one of its parent entities.


<table>
<tr>
<th valign="top">

Example Command



</th>
<th valign="top">

Command is Available for



</th>
<th valign="top">

Command is Executed in



</th>
</tr>
<tr>
<td valign="top">

`btp get accounts/available-environment`



</td>
<td valign="top">

 `--subaccount` 



</td>
<td valign="top">

The targeted subaccount



</td>
</tr>
<tr>
<td valign="top">

`btp update accounts/directory`



</td>
<td valign="top">

 `--directory` 



</td>
<td valign="top">

The parent directory of the targeted subaccount



</td>
</tr>
<tr>
<td valign="top">

`btp list accounts/available-region`



</td>
<td valign="top">

 `--global-account` 



</td>
<td valign="top">

The parent global account of the targeted subaccount



</td>
</tr>
<tr>
<td valign="top">

`btp list security/user`



</td>
<td valign="top">

`--global-account`

`--directory`

`--subaccount`



</td>
<td valign="top">

The targeted subaccount

> ### Tip:  
> To execute this command in a parent entity, use the `-dir` or `-ga` parameter without a value.



</td>
</tr>
<tr>
<td valign="top">

`btp list security/user --subaccount "1111XXXX-22XX-33XX-44XX-55555555XXXX"`



</td>
<td valign="top">

`--global-account`

`--directory`

`--subaccount`



</td>
<td valign="top">

The specified subaccount, which overrides the target



</td>
</tr>
</table>

> ### Remember:  
> To work in a different global account, you need to log in to this global account using `btp login`.

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

