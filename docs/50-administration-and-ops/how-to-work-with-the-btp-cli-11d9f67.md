<!-- loio11d9f67d2c68485ca2f435b955d3b85b -->

# How to Work with the btp CLI

Learn how to work with the SAP BTP command line interface \(btp CLI\). For example, how to log in, get help, and set a default context for commands.



<a name="loio11d9f67d2c68485ca2f435b955d3b85b__section_dw1_wg3_xkb"/>

## General Commands

```
`btp help`
```

```
`btp login`
```

```
`btp logout`
```

```
`btp target`
```

```
`btp enable autocomplete`
```

```
`btp disable autocomplete`
```



<a name="loio11d9f67d2c68485ca2f435b955d3b85b__section_pdm_xg3_xkb"/>

## General Options for Each Command

The following options are available for each command. They need to be typed right after the base call `btp`, and they can be combined \(for example, `btp --verbose --help list accounts/subaccount`. The `--help` option also works at the end of a command call.


<table>
<tr>
<th valign="top">

Options



</th>
<th valign="top">

 



</th>
</tr>
<tr>
<td valign="top">

--config



</td>
<td valign="top">

Specifies the location of the configuration file. See [Specify the Location of the Configuration File](specify-the-location-of-the-configuration-file-e57288d.md).



</td>
</tr>
<tr>
<td valign="top">

--info



</td>
<td valign="top">

Displays client and server versions, target, and context. Note that this option only works on its own \(`btp --info)` and cannot be added to other command calls. You can also just use `btp` to display this info. See [View Version and Current Context](view-version-and-current-context-9c29222.md).



</td>
</tr>
<tr>
<td valign="top">

--help



</td>
<td valign="top">

Displays help. See [Get Help](get-help-f8fd1e5.md).



</td>
</tr>
<tr>
<td valign="top">

--verbose



</td>
<td valign="top">

Prints tracing information for support. See [Troubleshooting and Support](troubleshooting-and-support-4023e15.md).



</td>
</tr>
<tr>
<td valign="top">

--format



</td>
<td valign="top">

Changes the output format of a command to JSON. See [Change the Output Format to JSON](change-the-output-format-to-json-dcb85b7.md).



</td>
</tr>
</table>

**Related Information**  


[Commands in the btp CLI](commands-in-the-btp-cli-a03a555.md "A list of all tasks and respective commands that are available in the SAP BTP command line interface (btp CLI).")

