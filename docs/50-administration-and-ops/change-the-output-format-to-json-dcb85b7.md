<!-- loiodcb85b7dea61432cbafaab4ce0ec9b08 -->

# Change the Output Format to JSON

Use the `--format json` option to change the output format of a command to JSON.



## Context

The standard output format of the btp CLI is text, formatted in a way that an interactive user of the btp CLI can easily read it. You can switch this to JSON output to make use of automation. Also, The JSON output often cludes more information than the respective text output, as the text output is optimized for human readability and therefore limited to the most relevant information.



## Procedure

1.  Start commands with `--format json`. Currently, the only valid value is `json`.

    ```
    `btp --format json list accounts/subaccount`
    ```




<a name="loiodcb85b7dea61432cbafaab4ce0ec9b08__result_iyy_c2k_qnb"/>

## Results



### Example with text output

```nocode
btp list accounts/subaccount
subaccounts in global account c8XXXX3d-6XX7-4XXb-8dXX-89XXXX372eXX...
subaccount id:                         display name:                              subdomain:                             region:        beta-enabled:   parent id:                             state:            state message:                                                                                                                                                    

88XXXX80-9844-4XX7-8XXd-beXXXX42bfb2   my-subaccount-1                            my-CF-subdomain1                       us10-TEST      false           c8XXXX3d-6XX7-4XXb-8dXX-89XXXX372eXX   OK                Subaccount created.                                                                                                                                               
ebXXXX3e-f3a2-4XXf-a080-3eXXXX9b9ced   my-subaccount-2                            my-CF-subdomain2                       us10-TEST      false           c8XXXX3d-6XX7-4XXb-8dXX-89XXXX372eXX   OK                Subaccount created.
```



### Example with JSON output

```nocode
btp list --format json accounts/subaccount
{
  "value": [

    {
      "guid": "88XXXX80-9844-4XX7-8XXd-beXXXX42bfb2",
      "displayName": "my-subaccount-1",
      "globalAccountGUID": "c8XXXX3d-6XX7-4XXb-8dXX-89XXXX372eXX",
      "parentGUID": "c8XXXX3d-6XX7-4XXb-8dXX-89XXXX372eXX",
      "parentType": "ROOT",
      "region": "us10-TEST",
      "subdomain": "my-CF-subdomain1",
      "betaEnabled": false,
      "usedForProduction": "UNSET",
      "description": null,
      "expiryDate": null,
      "state": "OK",
      "stateMessage": "Subaccount created.",
      "createdDate": 1602759737909,
      "createdBy": "name@email.com",
      "modifiedDate": 1602759737909,
      "zoneId": null
    },
    {
      "guid": "ebXXXX3e-f3a2-4XXf-a080-3eXXXX9b9ced",
      "displayName": "CF TEST",
      "globalAccountGUID": "c8XXXX3d-6XX7-4XXb-8dXX-89XXXX372eXX",
      "parentGUID": "c8XXXX3d-6XX7-4XXb-8dXX-89XXXX372eXX",
      "parentType": "ROOT",
      "region": "us10-TEST",
      "subdomain": "my-CF-subdomain2",
      "betaEnabled": false,
      "usedForProduction": "UNSET",
      "description": null,
      "expiryDate": null,
      "state": "OK",
      "stateMessage": "Subaccount created.",
      "createdDate": 1602760244477,
      "createdBy": "name@email.com",
      "modifiedDate": 1602760244477,
      "zoneId": null
    }
  ]
} 
```

**Related Information**  


[Get Help](get-help-f8fd1e5.md "There is extensive help in the btp CLI about every command. You can get help with the help action or the --help option.")

[View Version and Current Context](view-version-and-current-context-9c29222.md "To find out the current context you’re working in, run the command btp --info or simply btp.")

[Log in](log-in-e241b30.md "Log in with the btp CLI is on global account level.")

[Log out](log-out-9f1c87a.md "Logging out of the configured server removes all user-specific data from the configuration file.")

[Enable Command Autocompletion](enable-command-autocompletion-46355fa.md "Use command autocompletion to save keystrokes when entering command actions, group-object combinations, and their parameters in the SAP BTP command line interface (btp CLI).")

[Set a Target for Subsequent Commands with btp target](set-a-target-for-subsequent-commands-with-btp-target-720645a.md "Change the target for command calls to a directory, a subaccount, or the global account, by using the btp target command.")

[Specify the Location of the Configuration File](specify-the-location-of-the-configuration-file-e57288d.md "You can change the location of the configuration file by using the --config option or the environment variable.")

