<!-- loiodba4eb6547474ddfb903ac33316fb1f7 -->

# Change Configuration Settings

Change the configuration settings to customize the behavior of the btp CLI.



## Context

There are a few configuration settings that you can set to customize how the btp CLI works.

These settings are saved to the configuration file, which governs how the btp CLI works. You can have more than one configuration file for working in different accounts at the same time by logging in with the `--config PATH` option and then also providing it with each command call. See [Specify the Location of the Configuration File](specify-the-location-of-the-configuration-file-e57288d.md).

To find out where the configuration file is stored, use `btp --info`.



## Procedure

1.  To change a setting, run:

    `btp [OPTIONS] set config [--format FORMAT] [--verbose BOOL] [--login.sso MODE] [--login.securestore BOOL] [--login.showglobalaccounts BOOL] [--target.hierarchy BOOL] [--theme THEME]`


    <table>
    <tr>
    <td valign="top">
    
    **Parameter**
    
    </td>
    <td valign="top">
    
    **Description**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `--format FORMAT`
    
    </td>
    <td valign="top">
    
    The output format of commands. Valid values: text \(default\), json.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `--verbose BOOL`
    
    </td>
    <td valign="top">
    
    If set to true, command output includes tracing information for support. Valid values: false \(default\), true.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `--login.sso MODE`
    
    </td>
    <td valign="top">
    
    Single sign-on mode of `btp login`. Valid values: none \(default\), browser, manual. For example, if you want `btp login` to always open a browser for login at your identity provider, use `btp set config --login.sso browser`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `--login.securestore BOOL`
    
    </td>
    <td valign="top">
    
    If true, your login session will be stored in your OS secure store \(only macOS/Windows\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `--login.showglobalaccounts BOOL`
    
    </td>
    <td valign="top">
    
    If set to true, `btp login` will always prompt you to choose a global account.
    
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
    <tr>
    <td valign="top">
    
    `--theme THEME`
    
    </td>
    <td valign="top">
    
    Theme setting for the CLI. Use environment variable `NO_COLOR=true` to force the theme to 'none', regardless of this setting.
    
    </td>
    </tr>
    </table>
    
2.  To list the current settings, run:

    `btp [OPTIONS] list config`

3.  To reset individual or all settings back to their default values, run:

    `btp [OPTIONS] reset config [--format] [--verbose] [--login.sso] [--login.securestore] [--login.showglobalaccounts] [--target.hierarchy] [--theme] [--all]`


**Related Information**  


[Specify the Location of the Configuration File](specify-the-location-of-the-configuration-file-e57288d.md "You can change the location of the configuration file by using the --config option or the environment variable.")

