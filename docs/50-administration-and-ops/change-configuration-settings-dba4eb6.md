<!-- loiodba4eb6547474ddfb903ac33316fb1f7 -->

# Change Configuration Settings

Change the configuration settings to customize the behavior of the btp CLI.



## Context

There are a few configuration settings that you can set to customize how the btp CLI works. Currently, these settings include two options, which, instead of passing them with each command, can be set persistently: changing the output format to json and turning on verbose mode. The third setting is command-specific: you can configure how the `btp target` command behaves.

These settings are saved to the configuration file, which governs how the btp CLI works. You can have more than one configuration file for working in different accounts at the same time by logging in with the `--config PATH` option and then also providing it with each command call. See [Specify the Location of the Configuration File](specify-the-location-of-the-configuration-file-e57288d.md).

To find out where the configuration file is stored, use `btp --info`. Use the following commands to manage your configuration settings:



## Procedure

1.  To change a setting, run:

    ```
    btp [OPTIONS] set config [--format FORMAT] [--verbose BOOL] [--target.hierarchy BOOL]
    ```


    <table>
    <tr>
    <td valign="top">

    `--format FORMAT`


    
    </td>
    <td valign="top">

    The output format of commands. Valid values: text \(default\), json


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    `--verbose BOOL`


    
    </td>
    <td valign="top">

    If set to true, command output includes tracing information for support. Valid values: false \(default\), true


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    `--target.hierarchy BOOL`


    
    </td>
    <td valign="top">

    If set to true, `btp target` displays the full hierarchy of all global accounts. Valid values: false \(default\), true

    See [Set a Target for Subsequent Commands with btp target](set-a-target-for-subsequent-commands-with-btp-target-720645a.md).


    
    </td>
    </tr>
    </table>
    
2.  To list the current settings, run:

    ```
    btp [OPTIONS] list config
    ```

3.  To reset individual or all settings back to their default values, run:

    ```
    btp [OPTIONS] reset config [--format] [--verbose] [--target.hierarchy] [--all]
    ```


**Related Information**  


[Specify the Location of the Configuration File](specify-the-location-of-the-configuration-file-e57288d.md "You can change the location of the configuration file by using the --config option or the environment variable.")

