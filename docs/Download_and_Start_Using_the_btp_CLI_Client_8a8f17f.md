<!-- loio8a8f17f5fd334fb583438edbd831d506 -->

# Download and Start Using the btp CLI Client

To use the SAP BTP command line interface \(btp CLI\), you need to download the client first.



## Context

The client is available for 64-bit versions of the following operating systems:

-   Microsoft Windows

-   Apple macOS

-   Linux


> ### Note:  
> With the release of version 2.0.0 on March 25, 2021, the executable file of the CLI client was renamed from **sapcp** to **btp**. All commands remain compatible, and we will support the sapcp CLI until September 2021. However, this documentation and all examples inside refer to the **btp CLI**, and we recommend to download the latest btp CLI client from the [SAP Development Tools](https://tools.hana.ondemand.com/#cloud-btpcli) page. See [Migrating from sapcp to btp](Migrating_from_sapcp_to_btp_4f1fe8d.md).



## Procedure

1.  Download the appropriate client for your operating system from [SAP Development Tools](https://tools.hana.ondemand.com/#cloud-btpcli) or use the direct links to the latest version below. They are tar.gz archives that contain one executable file.

    -   [Latest version of CLI client for Microsoft Windows](https://tools.hana.ondemand.com/additional/btp-cli-windows-amd64-latest.tar.gz)

    -   [Latest version of CLI client for Apple macOS](https://tools.hana.ondemand.com/additional/btp-cli-darwin-amd64-latest.tar.gz)

    -   [Latest version of CLI client for Linux](https://tools.hana.ondemand.com/additional/btp-cli-linux-amd64-latest.tar.gz)

    > ### Note:  
    > You can also find older versions of the client at: [https://tools.hana.ondemand.com/\#cloud-btpcli](https://tools.hana.ondemand.com/#cloud-btpcli). In exceptional cases, when your client is too new for the configured server, an error message tells you which version you need and where to find it.

2.  Extract the client file \(for example: `btp.exe`\) to your local system and open a terminal session in the target folder.

    On Windows, you can use powershell or an external program, such as WinRar, to extract the tar.gz file. Once you've unpacked the executable, you can enter `cmd` in the address bar of the folder. This opens the command prompt in this folder.

    On macOS, you can open the tar.gz file by double-clicking in. Make sure that the executable is in your PATH, and open a terminal session.

    On Linux, use the terminal to open the tar.gz file with `tar -xzf btp-cli-linux-amd64-latest.tar.gz` and make sure the executable is in your PATH.

3.  Run `btp`. Note that you need read and write permissions in the target folder to run this executable.

    > ### Note:  
    > On macOS, opening btp CLI may be blocked because it is from "an unidentifed developer". Please refer to the macOS documentation to learn how to bypass this.

    You get a short welcome message with some useful information, such as the version of your client, how to display help, and how to log in.

    The CLI creates a configuration file \(`config.json`\) in your user data directory.

4.  Log in to your global account with `btp login`, which is interactive and will prompt for all required login information. Note that you need to provide the **subdomain of the global account** to log in. You can find this in the global account view in the cockpit. If you have more than one global account, see the *Switch Global Account* dialog. For details, see [Log in](Log_in_e241b30.md).

5.  Once you're logged in, familiarize yourself with the btp CLI, for example with [General Commands and Options in the btp CLI](General_Commands_and_Options_in_the_btp_CLI_11d9f67.md), [Command Syntax of the btp CLI](Command_Syntax_of_the_btp_CLI_69606f4.md), or simply by trying out a few commands, such as the following:

    ```
    `btp list accounts/subaccount`
    ```

    ```
    `btp list security/user`
    ```

    ```
    `btp get security/user "name@example.com"`
    ```

    ```
    `btp get accounts/global-account"`
    ```

    > ### Tip:  
    > You can use the command autocompletion feature in the btp CLI to save keystrokes when entering command actions, group-object combinations, and their parameters in the command line. For more information, see [Enable Command Autocompletion](Enable_Command_Autocompletion_46355fa.md).

6.  If you’re going to work in a subaccount of this global account, consider setting the default context to this subaccount using `btp target --subaccount *<ID\>*`. See [Set the Default Command Context](Set_the_Default_Command_Context_720645a.md). Tip: Use `btp list accounts/subaccount` to see the subaccounts of the global account.

7.  To find out the current context and version, use `btp`.


-   **[Get Updates](Get_Updates_e92aa78.md "We recommend updating the CLI client regularly to ensure that you can always use all new features. ")**  
We recommend updating the CLI client regularly to ensure that you can always use all new features.
-   **[Migrating from sapcp to btp](Migrating_from_sapcp_to_btp_4f1fe8d.md " The executable file was renamed from sapcp to btp, which makes it necessary to update
		all scripts to call btp instead of sapcp. ")**  
 The executable file was renamed from sapcp to btp, which makes it necessary to update all scripts to call btp instead of sapcp.

**Related Information**  


[Set the Default Command Context](Set_the_Default_Command_Context_720645a.md "Change the default context for all command calls to the global account, a directory, or a subaccount by using the btp target command.")

[Command Syntax of the btp CLI](Command_Syntax_of_the_btp_CLI_69606f4.md "Each command consists of the base call btp followed by a verb (the action), a combination of group and object, and parameters.")

[Get Help](Get_Help_f8fd1e5.md "Get help in the btp CLI with the --help option.")

[Commands in the btp CLI](Commands_in_the_btp_CLI_a03a555.md "A list of all tasks and respective commands that are available in the SAP BTP command line interface (btp CLI).")

[General Commands and Options in the btp CLI](General_Commands_and_Options_in_the_btp_CLI_11d9f67.md "Learn how to work with the SAP BTP command line interface (btp CLI). For example, how to log in, get help, and set a default context for commands.")

