<!-- loio899fe34d29c841e7bf78c70368592532 -->

# Passing JSON Parameters in the Command Line

Depending on the shell you use, the escaping rules are different. Here you'll find examples of correct escaping and quotes when passing JSON objects in the command line using different shells.

The table below gives an overview of the escaping rules in these commonly used shells.


<table>
<tr>
<th>

Shell



</th>
<th>

Correct Escaping and Quotes



</th>
</tr>
<tr>
<td>

Bash



</td>
<td>

Use `--parameter "VALUE"` and escape quotes with `\"` within `VALUE`

Use `--parameter 'VALUE'` and do not escape quotes within `VALUE`



</td>
</tr>
<tr>
<td>

Windows Command Prompt



</td>
<td>

Use `--param "VALUE"` and escape quotes with `\"` within `VALUE` 



</td>
</tr>
<tr>
<td>

Windows PowerShell



</td>
<td>

Use `--param 'VALUE'` and escape quotes with `\'` within `VALUE` 



</td>
</tr>
</table>

> ### Tip:  
> The CLI client provides examples in the command help for all commands. The examples that include JSON parameters use formatting that is compliant with Bash \(Unix/Linux operating system, macOS\) and Windows Command Prompt.

The command-line examples below are based on the following JSON:

```
`[
  {
    "key": "Key 1",
    "value": "Value 1"
  },
  {
    "key": "Key 2",
    "value": "Value 2"
  }
]
`
```



<a name="loio899fe34d29c841e7bf78c70368592532__section_qgg_gyd_hmb"/>

## Bash \(Linux, macOS\)

Option 1

```
`--parameter '[{"key": "Key 1","value": "Value 1"},{"key": "Key 2","value": "Value 2"}]'`
```

For example, when creating a subaccount \(`btp create accounts/subaccount`\) with custom properties `Landscape` = Dev and `Department` = HR, use the following syntax:

> ### Sample Code:  
> ```
> `--custom-properties '[{"key": "Landscape","value": "Dev"},{"key": "Department","value": "HR"}]'`
> ```

Option 2

```
`--parameter "[{\"key\":\"Key 1\",\"value\":\"Value 1\"},{\"key\":\"Key 2\",\"value\":\"Value 2\"}]"`
```

For example, when creating a subaccount \(`btp create accounts/subaccount`\) with custom properties `Landscape` = Dev and `Department` = HR, use the following syntax:

> ### Sample Code:  
> ```
> `--custom-properties "[{\"key\":\"Landscape\",\"value\":\"Dev\"},{\"key\":\"Department\",\"value\":\"HR\"}]"`
> ```



<a name="loio899fe34d29c841e7bf78c70368592532__section_gxx_dgr_vlb"/>

## Windows Command Prompt

```
`--parameter "[{\"key\":\"Key 1\",\"value\":\"Value 1\"},{\"key\":\"Key 2\",\"value\":\"Value 2\"}]"`
```

For example, when creating a subaccount \(`btp create accounts/subaccount`\) with custom properties `Landscape` = Dev and `Department` = HR, use the following syntax:

> ### Sample Code:  
> ```
> `--custom-properties "[{\"key\":\"Landscape\",\"value\":\"Dev\"},{\"key\":\"Department\",\"value\":\"HR\"}]"`
> ```



<a name="loio899fe34d29c841e7bf78c70368592532__section_ecd_ggr_vlb"/>

## Windows PowerShell

```
`--parameter '[{\"key\": \"Key 1\",\"value\": \"Value 1\"},{\"key\": \"Key 2\",\"value\": \"Value 2\"}]'`
```

For example, when creating a subaccount \(`btp create accounts/subaccount`\) with custom properties `Landscape` = Dev and `Department` = HR, use the following syntax:

> ### Sample Code:  
> ```
> `--custom-properties '[{\"key\": \"Landscape\",\"value\": \"Dev\"},{\"key\": \"Department\",\"value\": \"HR\"},{\"key\": \"Flagged\",\"value\": \"\"}]'`
> ```

**Related Information**  


[Command Syntax of the btp CLI](Command_Syntax_of_the_btp_CLI_69606f4.md "Each command consists of the base call btp followed by a verb (the action), a combination of group and object, and parameters.")

[Working with Global Accounts, Directories, and Subaccounts Using the btp CLI](Working_with_Global_Accounts,_Directories,_and_Subaccounts_Using_the_btp_CLI_85a683e.md "Use the SAP BTP command line interface (btp CLI) to manage operations with global accounts, directories, and subaccounts.")

[Working with External Resource Providers Using the btp CLI](Working_with_External_Resource_Providers_Using_the_btp_CLI_48d7688.md "Use the SAP BTP command line interface (btp CLI) to get details, or to create or delete resource provider instances in a global account.")

[Working with Environments Using the btp CLI](Working_with_Environments_Using_the_btp_CLI_48db155.md "Use the SAP BTP command line interface (btp CLI) to manage runtime environment instances in a subaccount. For example, enable the Cloud Foundry environment by creating a Cloud Foundry org (environment instance).")

