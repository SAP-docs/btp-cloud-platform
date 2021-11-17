<!-- loio69606f42743f46c29fa72c04e8c18674 -->

# Command Syntax of the btp CLI

Each command consists of the base call `btp` followed by a verb \(the action\), a combination of group and object, and parameters.

> ### Note:  
> With the release of version 2.0.0 on March 25, 2021, the executable file of the CLI client was renamed from **sapcp** to **btp**. All commands remain compatible, and we will support the sapcp CLI until September 2021. However, this documentation and all examples inside refer to the **btp CLI**, and we recommend to download the latest btp CLI client from the [SAP Development Tools](https://tools.hana.ondemand.com/#cloud-btpcli) page. See [Migrating from sapcp to btp](Migrating_from_sapcp_to_btp_4f1fe8d.md).

The btp CLI uses the following syntax:

```
`**btp \[OPTIONS\] ACTION GROUP/OBJECT \[PARAMS\]**`
```

The commands are ordered in groups. Words in caps are placeholders, and brackets \[ \] denote optionality. Here's is one example with the help option and no parameters before we outline the entire syntax:

> ### Sample Code:  
> ```
> `**btp --help list accounts/subaccount **`
> ```

-   `btp` is the base call to start each command

-   OPTIONS can be added to each command, for example to get help `--help` or execute a command in verbose mode `--verbose`. Note that the `--help` option can also be placed at the end of a command.

-   ACTION is the verb. Depending on the GROUP/OBJECT combination, different verbs are available, such as `get`, `list`,`create`, `delete`, `assign`, `unassign`, `add`, `remove`. For a complete list, use `btp --help`.

-   The GROUP/OBJECT combination specifies the entity that the action is carried out on. For example, all commands related to users and their authorizations belong to the **security** group, in which **objects** such as role, role-collection, and user are available.

-   PARAMETERS are passed with most commands. Some commands have one positional parameter, which is entered directly after the command. All further parameters have a key and can be optional. The command help specifies the optional parameters as such. For example, in `btp assign security/role-collection "Global Account Administrator" --to-user example@mail.com --of-idp my-idp`, "Global Account Administrator" is the positional parameter, and the other two parameters have keys.




> ### Note:  
> The commands that you type into the command-line are interpreted and executed by the shell. Make sure you’re familiar with your shell to avoid unexpected interferences. For examples of correct escaping, see [Passing JSON Parameters in the Command Line](Passing_JSON_Parameters_in_the_Command_Line_899fe34.md).

> ### Tip:  
> You can use the command autocompletion feature in the btp CLI to save keystrokes when entering commands actions, group-object combinations, and their parameters in the command line. For more information, see [Enable Command Autocompletion](Enable_Command_Autocompletion_46355fa.md).



<a name="loio69606f42743f46c29fa72c04e8c18674__section_uzv_sxz_mlb"/>

## A Few Commands to Get Started

Here are a few commands for you to try out once you're logged in \([Log in](Log_in_e241b30.md)\):

```
`btp list accounts/subaccount`
```

```
`btp list security/user`
```

```
`btp get security/user "name@example.com"`
```

```
`btp list accounts/subscription`
```



In this example, we assign the **Global Account Administrator** role collection to user **name@example.com** and try out some options.

Using the `--help` option to display command-specific help to learn how to use the command:

```
`btp --help assign security/role-collection`
```

```
`btp assign security/role-collection --help`
```

Command with positional parameter and one mandatory parameter:

```
`btp assign security/role-collection "Global Account Administrator" --to-user "name@example.com"`
```

Command with positional parameter, mandatory parameter, and optional parameter:

```
`btp assign security/role-collection "Global Account Administrator" --to-user "name@example.com" --of-idp "my-idp"`
```

The same command in verbose mode:

```
`btp --verbose assign security/role-collection "Global Account Administrator" --to-user "name@example.com" --of-idp "my-idp"`
```

**Related Information**  


[Set the Default Command Context](Set_the_Default_Command_Context_720645a.md "Change the default context for all command calls to the global account, a directory, or a subaccount by using the btp target command.")

