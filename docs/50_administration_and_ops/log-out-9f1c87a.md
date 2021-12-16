<!-- loio9f1c87a3068f44ef90a903a9f45f986a -->

# Log out

Logging out of the configured server removes all user-specific data from the configuration file.



## Context

Once you're finished using the btp CLI and you want to ensure that your locally stored credentials are immediately deleted, you can run the logout command. If you choose not to log out, your credentials will expire 24 hours after you last command execution, but the next time you log in, the btp CLI will propose your current subdomain and user so you won't have to type it in again.



## Procedure

1.  To log out, use `btp logout`.

    This terminates your active logout session and ensures that all user-specific data is removed. The next time you log in, you will have to type in the subdomain of the global account and your user.


**Related Information**  


[Get Help](get-help-f8fd1e5.md "There is extensive help in the btp CLI about every command. You can get help with the help action or the --help option.")

[View Version and Current Context](view-version-and-current-context-9c29222.md "To find out the current context you’re working in, run the command btp --info or simply btp.")

[Log in](log-in-e241b30.md "Log in with the btp CLI is on global account level.")

[Enable Command Autocompletion](enable-command-autocompletion-46355fa.md "Use command autocompletion to save keystrokes when entering command actions, group-object combinations, and their parameters in the SAP BTP command line interface (btp CLI).")

[Set the Default Command Context](set-the-default-command-context-720645a.md "Change the default context for all command calls to the global account, a directory, or a subaccount by using the btp target command.")

[Change the Output Format to JSON](change-the-output-format-to-json-dcb85b7.md "Use the --format json option to change the output format of a command to JSON.")

[Specify the Location of the Configuration File](specify-the-location-of-the-configuration-file-e57288d.md "You can change the location of the configuration file by using the --config option or the environment variable.")

[Log in](log-in-e241b30.md "Log in with the btp CLI is on global account level.")

