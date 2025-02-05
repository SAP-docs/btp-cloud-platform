<!-- loio46355fab22814944bedf449a6c953369 -->

# Enable Command Autocompletion

Use command autocompletion to save keystrokes when entering command actions, group-object combinations, and their parameters in the SAP BTP command line interface \(btp CLI\).



## Context

Autocompletion in btp CLI currently supports the following shells:

-   Bash
-   PowerShell
-   Zsh

> ### Note:  
> The respective shell must be installed on your operating system before enabling autocomplete. Additionally, the btp CLI executable must be available on the `path` for autocompletion to initialize. To install it on the `path`, follow the steps outlined in[Download and Start Using the btp CLI Client](download-and-start-using-the-btp-cli-client-8a8f17f.md#loio8a8f17f5fd334fb583438edbd831d506).

Once autocomplete is enabled \(it’s disabled by default\), you use the autocomplete feature as follows in the command line:

-   Enter a partial command action, group-object combination, or parameter, and then press the [Tab\] key. The command line either automatically completes your command or, when there’s more than one option available, it displays a list of suggested command actions/options/parameters.

-   When a suggestion list is displayed, depending on your shell, use the [Tab\] or arrow keys to move through the list and press [Enter\] to make a selection.




### Examples

The following examples show various ways that you can use autocompletion:

-   Enter `btp` and press [Tab\] to display all available actions:

    ```
    ./btp TAB
    add          create       enable       list         logout       register     subscribe    unassign     unsubscribe
    assign       delete       get          login        move         remove       target       unregister   update 
    
    ```

-   Partially enter `btp cre` and press [Tab\] to autocomplete the command to `btp create`. Then, press [Tab\] again to display a suggested list of group-object combinations:

    ```
    ./btp create TAB
    accounts/directory             accounts/resource-provider     security/role                  services/binding
    accounts/environment-instance  accounts/subaccount            security/role-collection       services/instance
    
    ```

-   Partially enter a group and press [Tab\] to display a suggested list of objects:

    ```
    ./btp create accountsTAB
    accounts/directory             accounts/environment-instance  accounts/resource-provider     accounts/subaccount
    ```

-   Partially enter a parameter and press [Tab\] to display a suggested list of parameters:

    ```
    ./btp create accounts/subaccount -TAB
    --beta-enabled
    --custom-properties
    --description
    --directory
    --display-name
    --global-account
    --region
    --subaccount-admins
    --subdomain
    --used-for-production
    ```




<a name="loio46355fab22814944bedf449a6c953369__steps_mdz_lzw_xmb"/>

## Procedure

1.  Use <code>btp enable autocomplete <i class="varname">&lt;SHELL&gt;</i></code> to enable command autocompletion for a specified shell.

    The valid values for the supported shells are:

    -   `bash`
    -   `powershell`
    -   `zsh`

    > ### Sample Code:  
    > `btp enable autocomplete zsh`

2.  Enter the option of your choice.

    To enable autocompletion, the startup file \(RC file\) of your shell is modified to load the available commands and parameters. The client looks for this RC file in your system and proposes possible files. You can choose to accept a proposal or specify a different RC file. To specify a custom path, first choose "Custom" and then enter the full path of the RC file to use. If no RC file is found, the clients prints an error message with the full path of the missing file so that you can create it and run the enable command again.

    For example:

    ```
    ./btp enable autocomplete powershell
    Which RCFile should be used for the installation?
    1: C:\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1
    2: Custom
    Enter option>2
    Enter the full path of your RCFile>C:\Documents\WindowsPowerShell\Microsoft.PowerShell_my-custom-profile.ps1
    ```

3.  Start a new terminal session to activate the installed autocomplete script.




<a name="loio46355fab22814944bedf449a6c953369__result_l3y_pyw_xmb"/>

## Results

The autocompletion option remains enabled in future sessions in your current client, until you disable it. To disable command autocompletion, run the following command:

```
btp disable autocomplete <SHELL>
```

You can run either `btp` or `btp --info` to see if command autocompletion is currently enabled and where the autocomplete RC file for your shell is located. If you don't see a line specifying the location of the autocomplete script, then it’s disabled.

> ### Tip:  
> If you see a discrepancy between the version of the autocomplete script and the client, the update of the autocomplete script might have failed. In such a case, try to disable and enable the autocomplete feature again.

Whenever you start a new btp CLI terminal session, the autocomplete suggestions are automatically updated to include the latest commands.

If disabling the command autocompletion fails or you have uninstalled the btp CLI client without disabling autocompletion, you can manually remove traces of the autocomplete installation in your shell initialization file \(RC or profile file depending on your shell\) by deleting the section in your RC file from `Begin SAP BTP command line interface autocomplete`to `End SAP BTP command line interface autocomplete`.

