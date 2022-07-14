<!-- loio9f1c87a3068f44ef90a903a9f45f986a -->

# Log out

Logging out of the configured server removes all user-specific data from the configuration file.



## Context

Once you're finished using the btp CLI and you want to ensure that your locally stored credentials are immediately deleted, you can run the logout command. If you choose not to log out, your credentials will expire 24 hours after you last command execution, but the next time you log in, the btp CLI will propose your current subdomain and user so you won't have to type it in again.



## Procedure

1.  To log out, use `btp logout`.

    This terminates your active logout session and ensures that all user-specific data is removed. The next time you log in, you will have to type in the subdomain of the global account and your user.


**Related Information**  


[Log in](log-in-e241b30.md "Log in with the btp CLI is on global account level.")

