<!-- loio69606f42743f46c29fa72c04e8c18674 -->

# Command Syntax of the btp CLI

Each command consists of the base call `btp` followed by a verb \(the action\), a combination of group and object, and parameters.

The btp CLI uses the following syntax:

```
btp [OPTIONS] ACTION GROUP/OBJECT [PARAMS]
```

The commands are ordered in groups and you need to specify the object on which you want to carry out an action by the group/object combination. Words in caps are placeholders, and brackets \[ \] denote optionality. Optionally, you can pass options with a command call. Here's is one example with the verbose option and no parameters before we outline the entire syntax:

> ### Sample Code:  
> ```
> btp --verbose list accounts/subaccount
> ```

-   `btp` is the base call to start each command

-   OPTIONS can be added to each command, for example `--format json` to change the output format to json, or `--verbose` to execute a command in verbose mode. For details, see [How to Work with the btp CLI](how-to-work-with-the-btp-cli-11d9f67.md).

-   ACTION is the verb. Depending on the GROUP/OBJECT combination, different verbs are available, such as `get`, `list`,`create`, `delete`, `assign`, `unassign`, `add`, `remove`. For a complete list, use `btp help`. To find out which commands are available for a specific action, use `btp help ACTION`, for example, `btp help list`.

-   Special ACTION: the `help` ACTION. You can always place `help` at the beginning of a command and still add further parts of the command, such as the ACTION or GROUP or GROUP/OBJECT combination for which you want to call help. See [Get Help for btp CLI](get-help-for-btp-cli-f8fd1e5.md).

-   The GROUP/OBJECT combination specifies the entity that the action is carried out on. For example, all commands related to users and their authorizations belong to the **security** group, in which **objects** such as role, role-collection, and user are available. There are currently three groups:

    -   accounts: Objects related to the account model, subscriptions, and environments

    -   security: Authorization objects and users

    -   services: Objects related to SAP Service Manager


    To get help on a particular group, use `btp help GROUP`, for example `btp hep accounts`. This will display all objects and related actions available in that group.

-   PARAMETERS are passed with most commands. With `btp login`, for example, you don't have to pass parameters up front, but you'll be prompted to enter them. The same applies to the `btp target` command. And `btp logout` does not need parameters, as it will log out the current user from the global account. Some commands have one positional parameter, which is entered directly after the command. All further parameters have a key and can be optional. The command help specifies the optional parameters as such. For example, in `btp assign security/role-collection "Global Account Administrator" --to-user example@mail.com --of-idp my-idp`, "Global Account Administrator" is the positional parameter, and the other two parameters have keys.

    You may encounter issues with certain parameter values that start with a `-`, as they can be mistaken for parameter names instead of values. It is recommended to use a `=` to separate parameters and values when a value begins with `-`. For example, if your value for parameter `--user` is`-username-,` please use `--user="-username-"`.




> ### Note:  
> The commands that you type into the command line are interpreted and executed by the shell. Make sure you’re familiar with your shell to avoid unexpected interferences. For examples of correct escaping, see [Passing JSON Parameters on the Command Line](passing-json-parameters-on-the-command-line-899fe34.md).

> ### Tip:  
> You can use the command autocompletion feature in the btp CLI to save keystrokes when entering commands actions, group-object combinations, and their parameters in the command line. For more information, see [Enable Command Autocompletion](enable-command-autocompletion-46355fa.md).



<a name="loio69606f42743f46c29fa72c04e8c18674__section_uzv_sxz_mlb"/>

## A Few Commands to Get Started

Here are a few commands for you to try out once you're logged in \([Log in](log-in-e241b30.md)\):

```
btp list accounts/subaccount
```

```
btp list security/user
```

```
btp get security/user "name@example.com"
```

```
btp list accounts/subscription
```



## Example

In this example, we assign the **Global Account Administrator** role collection to user **name@example.com** and try out some options.

Use `help` or `--help` to display command-specific help to learn how to use the command:

```
btp help assign security/role-collection
```

```
btp assign security/role-collection --help
```

```
btp --help assign security/role-collection
```

Command with positional parameter and one mandatory parameter:

```
btp assign security/role-collection "Global Account Administrator" --to-user "name@example.com"
```

Command with positional parameter, mandatory parameter, and optional parameter:

```
btp assign security/role-collection "Global Account Administrator" --to-user "name@example.com" --of-idp "my-idp"
```

The same command in verbose mode:

```
btp --verbose assign security/role-collection "Global Account Administrator" --to-user "name@example.com" --of-idp "my-idp"
```

**Related Information**  


[btp CLI Command Reference](https://help.sap.com/docs/BTP/btp-cli/intro.html)

