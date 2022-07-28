<!-- loio8a8f17f5fd334fb583438edbd831d506 -->

# Download and Start Using the btp CLI Client

To use the SAP BTP command line interface \(btp CLI\), you need to download the client first.



## Context

The client is available for 64-bit versions of the following operating systems:

-   Microsoft Windows

-   Apple macOS

-   Linux




## Procedure

1.  Download the appropriate client for your operating system from [SAP Development Tools](https://tools.hana.ondemand.com/#cloud-btpcli) or use the direct links to the latest version below. They are tar.gz archives that contain one executable file.

    -   [Latest version of CLI client for Microsoft Windows](https://tools.hana.ondemand.com/additional/btp-cli-windows-amd64-latest.tar.gz)

    -   [Latest version of CLI client for Apple macOS](https://tools.hana.ondemand.com/additional/btp-cli-darwin-amd64-latest.tar.gz)

    -   [Latest version of CLI client for Linux](https://tools.hana.ondemand.com/additional/btp-cli-linux-amd64-latest.tar.gz)


    > ### Note:  
    > You can also find older versions of the client at: [https://tools.hana.ondemand.com/\#cloud-btpcli](https://tools.hana.ondemand.com/#cloud-btpcli). In exceptional cases, when your client is too new for the configured server, an error message tells you which version you need and where to find it.

2.  Extract the client file \(for example: `btp.exe`\) to your local system and open a terminal session in the target folder.

    On Windows, you can use powershell or an external program, such as WinRar, to extract the tar.gz file. Once you've unpacked the executable, you can enter `cmd` or `powershell` in the address bar of the folder. This opens the command prompt or PowerShell in this folder.

    On macOS, you can open the tar.gz file by double-clicking in. Make sure that the executable is in your PATH, and open a terminal session.

    On Linux, use the terminal to open the tar.gz file with `tar -xzf btp-cli-linux-amd64-latest.tar.gz` and make sure the executable is in your PATH.

3.  \(Optional\) If you have a proxy server configured in your environment, you need to specify its address and port as environment variable `HTTPS_PROXY` or `https_proxy` to access SAP BTP. For example, `HTTPS_PROXY=https://my-https-proxy:1234`.

    The specified proxy server is then used for HTTPS requests, unless overriden by the `NO_PROXY` or `no_proxy`, environment variables, which define a comma-separated list of hosts to be excluded from proxying.

4.  Run `btp`. Note that you need read and write permissions in the target folder to run this executable.

    > ### Note:  
    > On macOS, opening btp CLI may be blocked because it is from "an unidentifed developer". Please refer to the macOS documentation to learn how to bypass this.

    You get a short welcome message with some useful information, such as the version of your client, how to display help, and how to log in.

    The CLI creates a configuration file \(`config.json`\) in your user data directory.

5.  Log in to your global account with `btp login`, which is interactive and will prompt for all required login information. Note that you need to enter the btp CLI server url \(`https://cpcli.cf.eu10.hana.ondemand.com`\) and the **subdomain of the global account** to log in. You can find this global account subdomain in the global account view in the cockpit. If you have more than one global account, see the *Switch Global Account* dialog. For details, see [Log in](log-in-e241b30.md).

6.  Once you're logged in, familiarize yourself with the btp CLI, for example with [How to Work with the btp CLI](how-to-work-with-the-btp-cli-11d9f67.md), [Command Syntax of the btp CLI](command-syntax-of-the-btp-cli-69606f4.md), or simply by trying out a few commands, such as the following:

    ```
    btp list accounts/subaccount
    ```

    ```
    btp list security/user
    ```

    ```
    btp get security/user "name@example.com"
    ```

    ```
    btp get accounts/global-account"
    ```

    > ### Tip:  
    > You can use the command autocompletion feature in the btp CLI to save keystrokes when entering command actions, group-object combinations, and their parameters in the command line. For more information, see [Enable Command Autocompletion](enable-command-autocompletion-46355fa.md).

7.  If you’re going to work in a subaccount of this global account, consider setting the target to this subaccount using <code>btp target --subaccount <i class="varname">&lt;ID&gt;</i></code>. See [Set a Target for Subsequent Commands with btp target](set-a-target-for-subsequent-commands-with-btp-target-720645a.md). Tip: Use `btp list accounts/subaccount` to display the subaccount IDs of the global account.

8.  To find out the current context, target, and version, use `btp`.


**Related Information**  


[How to Work with the btp CLI](how-to-work-with-the-btp-cli-11d9f67.md "Learn how to work with the SAP BTP command line interface (btp CLI). For example, how to log in, get help, and set a default context for commands.")

[Command Syntax of the btp CLI](command-syntax-of-the-btp-cli-69606f4.md "Each command consists of the base call btp followed by a verb (the action), a combination of group and object, and parameters.")

[Set a Target for Subsequent Commands with btp target](set-a-target-for-subsequent-commands-with-btp-target-720645a.md "Set the target for command calls to a subaccount, a directory, or the global account with the btp target command.")

[btp CLI Command Reference](https://help.sap.com/docs/BTP/btp-cli/intro.html)

