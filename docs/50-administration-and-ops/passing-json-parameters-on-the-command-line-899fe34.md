<!-- loio899fe34d29c841e7bf78c70368592532 -->

# Passing JSON Parameters on the Command Line

Depending on the shell you use, the escaping rules are different. Here you'll find examples of correct escaping and quotes when passing JSON objects on the command line using different shells.

The table below gives an overview of the escaping rules in these commonly used shells. VALUE refers to one single line in json.


<table>
<tr>
<th valign="top">

Shell



</th>
<th valign="top">

Correct Escaping and Quotes



</th>
</tr>
<tr>
<td valign="top">

Bash



</td>
<td valign="top">

Use `--parameter "VALUE"` and escape quotes with `\"` within `VALUE`

or

Use `--parameter 'VALUE'` and do not escape quotes within `VALUE`



</td>
</tr>
<tr>
<td valign="top">

Windows Command Prompt



</td>
<td valign="top">

Use `--param "VALUE"` and escape quotes with `\"` within `VALUE` 



</td>
</tr>
<tr>
<td valign="top">

Windows PowerShell



</td>
<td valign="top">

Use `--param "VALUE"` and escape quotes with `\"` within `VALUE` 



</td>
</tr>
</table>

> ### Tip:  
> The CLI client provides examples in the command help for all commands. The examples that include JSON parameters use formatting that is compliant with Bash \(Unix/Linux operating system, macOS\) and Windows Command Prompt.

The command-line examples in this chapter are based on the following JSON:

```
{
    "Key1": ["Value1"],
    "Key2": ["Value1", "Value2"]
}

```



<a name="loio899fe34d29c841e7bf78c70368592532__section_qgg_gyd_hmb"/>

## Bash \(Linux, macOS\)

Option 1

```
--parameter "{\"Key1\":[\"Value1\"],\"Key2\":[\"Value1\", \"Value2\"]}"
```

For example, when creating a subaccount \(`btp create accounts/subaccount`\) with labels `Department` = Sales and `Contacts` = name1@example.com and name2@example.com, use the following syntax:

> ### Sample Code:  
> ```
> btp create account/subaccount --display-name "my-subaccount" --region us10 --subdomain "my-subdomain" --labels "{\"Department\":[\"Sales\"],\"Contacts\":[\"name1@example.com\", \"name2@example.com\"]}"
> ```



Option 2

```
--parameter '{"Key1": ["Value1"], "Key2": ["Value1", "Value2"]}'
```

For example, when creating a subaccount \(`btp create accounts/subaccount`\) with labels `Department` = Sales and `Contacts` = name1@example.com and name2@example.com, use the following syntax:

> ### Sample Code:  
> ```
> btp create account/subaccount --display-name "my-subaccount" --region us10 --subdomain my-subdomain --labels '{"Department": ["Sales"],"Contacts": ["name1@example.com", "name2@example.com"]}'
> ```



<a name="loio899fe34d29c841e7bf78c70368592532__section_gxx_dgr_vlb"/>

## Windows Command Prompt

```
--parameter "{\"Key1\":[\"Value1\"],\"Key2\":[\"Value1\", \"Value2\"]}"
```

For example, when creating a subaccount \(`btp create accounts/subaccount`\) with labels `Department` = Sales and `Contacts` = name1@example.com and name2@example.com, use the following syntax:

> ### Sample Code:  
> ```
> btp create account/subaccount --display-name "my-subaccount" --region us10 --subdomain "my-subdomain" --labels "{\"Department\":[\"Sales\"],\"Contacts\":[\"name1@example.com\", \"name2@example.com\"]}"
> ```



<a name="loio899fe34d29c841e7bf78c70368592532__section_ecd_ggr_vlb"/>

## Windows PowerShell

```
--parameter '{\"Key1\":[\"Value1\"],[\"Key2\":\"Value1\", \"Value2\"]}'
```

For example, when creating a subaccount \(`btp create accounts/subaccount`\) with labels `Department` = Sales and `Contacts` = name1@example.com and name2@example.com, use the following syntax:

> ### Sample Code:  
> ```
> ./btp create account/subaccount --display-name "my-subaccount" --region us10 --subdomain my-subdomain --labels '{\"Department\":[\"Sales\"],\"Contacts\":[\"name1@example.com\", \"name2@example.com\"]}'
> ```



<a name="loio899fe34d29c841e7bf78c70368592532__section_ls4_vvz_cqb"/>

## Passing JSON Parameters as Files

You can also transfer JSON parameters by providing the full path to a JSON file. For example:

```
btp create services/binding --name my-binding-name --instance-name my-service-instance-name --parameters "<your-user-directory>/Documents/parameters.json"
```

**Related Information**  


[Command Syntax of the btp CLI](command-syntax-of-the-btp-cli-69606f4.md "Each command consists of the base call btp followed by a verb (the action), a combination of group and object, and parameters.")

[Working with Global Accounts, Directories, and Subaccounts Using the btp CLI](working-with-global-accounts-directories-and-subaccounts-using-the-btp-cli-85a683e.md "Use the SAP BTP command line interface (btp CLI) to manage operations with global accounts, directories, and subaccounts.")

[Working with External Resource Providers Using the btp CLI](working-with-external-resource-providers-using-the-btp-cli-48d7688.md "Use the SAP BTP command line interface (btp CLI) to get details, or to create or delete resource provider instances in a global account.")

[Working with Environments Using the btp CLI](working-with-environments-using-the-btp-cli-48db155.md "Use the SAP BTP command line interface (btp CLI) to manage runtime environment instances in a subaccount. For example, enable the Cloud Foundry environment by creating a Cloud Foundry org (environment instance).")

