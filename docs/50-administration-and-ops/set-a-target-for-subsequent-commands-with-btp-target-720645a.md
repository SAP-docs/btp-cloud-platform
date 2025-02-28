<!-- loio720645a3ed3945bd8d97a670b948ac07 -->

# Set a Target for Subsequent Commands with `btp target`

Set the target for command calls to a subaccount, a directory, or a global account with the `btp target` command.



## Context

During login, the btp CLI asks you for the global account you want to log in to and this global account is then the target. This means that commands are executed in this global account unless you specify otherwise via a parameter. There are two typical use cases for the target command:

-   If you know that you need to work in a particular subaccount or directory, you can change the target, so that you won't have to specify that subaccount's or directory's ID as a parameter with every command call.

-   If you want to switch to another global account, you can do so by setting the target to this global account without logging in again.


By setting the target to a subaccount or directory, you also target its parent entities, that is, the **target hierarchy**. If no parameter is specified in a command call, the btp CLI will execute the command in the innermost targeted entity where a command is applicable. If a subaccount is targeted that is inside a directory and the command is not available on subaccount level, it will be executed in the parent directory \(if it's a directory command\) or in the parent global account \(if it's a global account command\). This can be useful, for example, if you have targeted a subaccount, but want to update its parent directory. You can then execute `btp update accounts/directory` without specifying the directory ID.

To see the current target, use `btp --info` or simply `btp`.

To explicitly execute a command in a parent entity instead of in the target, you can specify this with '-dir' or '-ga' parameters without a value. The value is then taken from the target hierarchy. This can be useful, for example, if you have targeted a subaccount, but want to list the users of the parent directory. You can then execute `btp list security/user -dir`. Note, however, that this command is only available on a directory level if the directory is enabled to manage authorizations.

Usage: `btp [OPTIONS] target [PARAMS]`



## Procedure

1.  Use `btp target` to set the target for subsequent commands.

    -   Run the command without parameters to see the children, siblings and parent of you current target. You can then select your target or navigate up and down.
    -   Enter `--hierarchy` as parameter to see all your global accounts with their entire account hierarchies. You can then select your target from this list.

        > ### Tip:  
        > If you like the `--hierarchy` parameter and would like to make it the default for the target command, you can define it as a configuration setting with `btp set config --target.hierarchy true`. If you then run `btp target`, the entire hierarchy of all your global accounts is shown.

    -   Specify the subaccount, directory, or global account you want to target as described in the next step.

2.  Enter one of the following parameters:


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
    
    The subdomain of the global account to be targeted.
    
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

The CLI client displays the current target as a hierarchy. To execute a command in the targeted entity, you can omit the corresponding parameter.



## Example

A global account can group together different directories and subaccounts that the global account administrator makes available to users. CLI commands can be executed on all levels of this account hierarchy, that is in the global account, a directory, or a subaccount, usually specified by the above-mentioned parameters. The table below shows some example commands, and explains in which account entity they can be executed and how the target mechanism can be used.

Let's look at a global account that contains a directory with a targeted subaccount. With `btp`, the current target hierarchy is displayed like this:

```
Current target:
  My Global Account (global account, subdomain: cee12xx112345-ga)
  └─ My Directory (directory, ID: 371eXXXX-55XX-40XX-b3XX-e9947ed9XXXX)
     └─ My Subaccount (subaccount, ID: d8aeXXXX-74XX-49XX-89XX-f058029eXXXX)

```

Now, when you run commands without specifying an account entity as parameter, they are executed in the targeted subaccount or in one of its parents.


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

`[directory] ID`

Note that the directory ID is a positional parameter in this command. You can omit it when a subaccount inside the directory is targeted: `btp update accounts/directory [directory ID]`.

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

**Related Information**  


[btp CLI Command Reference](https://help.sap.com/docs/BTP/btp-cli/intro.html)

[Global Accounts](../10-concepts/account-model-8ed4a70.md#loioc165d95ee700407eb181770901caec94 "A global account is the realization of a contract you or your company has made with SAP.")

