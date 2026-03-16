<!-- loiod95c08ad1e694317bcae3470a77a6a7d -->

# Theme Configuration for the btp CLI

Customize the visual theme of the SAP BTP Command Line Interface \(btp CLI\).



## Context

You can control the visual appearance of the SAP BTP Command Line Interface \(btp CLI\) output by using the theme configuration parameter.



## Procedure

1.  **Available Themes**

    The following values are supported:

    -   **default** \(default\): applies the SAP-themed visual style to the CLI output.
    -   **none**: applies the standard CLI appearance without additional theming.

2.  **Set the Theme**

    To configure the theme, use:

    ```
    btp set config --theme=<value>
    ```

    Examples:

    -   `btp set config --theme=default`
    -   `btp set config --theme=none`

3.  **Reset the Theme Configuration**

    To reset the theme setting to its default value, run:

    ```
    btp reset config –theme
    ```

4.  **NO\_COLOR Environment Variable**

    If the NO\_COLOR environment variable is set to true, any configured theme is ignored and the CLI output is displayed without theming.

    When `NO_COLOR=true` is set, it overrides the `--theme` configuration.


**Related Information**  


[Change Configuration Settings](change-configuration-settings-dba4eb6.md "Change the configuration settings to customize the behavior of the btp CLI.")

