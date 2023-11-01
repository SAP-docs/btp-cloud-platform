<!-- loio8a8f17f5fd334fb583438edbd831d506 -->

# Download and Start Using the btp CLI Client

To use the SAP BTP command line interface \(btp CLI\), you need to download the client first.



## Context

The client is available for 64-bit versions of the following operating systems:

-   Microsoft Windows \(amd64\)

-   Apple macOS \(amd64 and arm64\)

-   Linux \(amd64 and arm64\)


Each released client version is supported for at least a year. If a client is deprecated, you are notified six months before it stops working in the [What's New for SAP Business Technology Platform](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?Component=SAP%20BTP%20Command%20Line%20Interface&locale=en-US&version=Cloud) page on SAP Help Portal \(filter for *SAP BTP Command Line Interface\)* as well as in the client itself. Most of the updates to the btp CLI don't require a new client installation, but are made available through updates of the btp CLI server, so that you can use them in your installed version of the client.



## Procedure

1.  Download the appropriate client for your operating system from [SAP Development Tools](https://tools.hana.ondemand.com/#cloud-btpcli) or use the links in the table below. They are tar.gz archives that contain one executable file.


    <table>
    <tr>
    <th valign="top">

    Operating System
    
    </th>
    <th valign="top">

    Link to latest version
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Microsoft Windows
    
    </td>
    <td valign="top">
    
    [amd64](https://tools.hana.ondemand.com/additional/btp-cli-windows-amd64-latest.tar.gz) 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Apple macOS
    
    </td>
    <td valign="top">
    
    [amd64](https://tools.hana.ondemand.com/additional/btp-cli-darwin-amd64-latest.tar.gz) | [arm64](https://tools.hana.ondemand.com/additional/btp-cli-darwin-arm64-latest.tar.gz) 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Linux
    
    </td>
    <td valign="top">
    
    [amd64](https://tools.hana.ondemand.com/additional/btp-cli-linux-amd64-latest.tar.gz) | [arm64](https://tools.hana.ondemand.com/additional/btp-cli-linux-arm64-latest.tar.gz) 
    
    </td>
    </tr>
    </table>
    
2.  Extract the client file from the tar.gz archive.

    Linux: Use the terminal to open the tar.gz file with `tar -xzf btp-cli-linux-amd64-latest.tar.gz`.

    macOS: Open the tar.gz file by double-clicking in.

    Windows: Use powershell or an external program, such as WinRar, to extract the tar.gz file. Tip: Once you've unpacked the executable, you can enter `cmd` or `powershell` in the address bar of the folder. This opens the command prompt or PowerShell in this folder. Or proceed with the next step in order to enable calling `btp` from any location on your system.

3.  Copy the client executable from the unpacked folder to a directory of your choice. We recommend the following, because it ensures that you can call `btp` system wide, i.e. that it is in your PATH:

    Linux: `/usr/local/bin`

    macOS: `/usr/local/bin`

    Windows: `C:/Users/<your-user>`

    In the Windows search, enter `Environment Variable` and open the *System Properties*. On the **Advanced** tab, open **Environment Variables**. Under **User Variables**, open the **Path** entry and add the file location of the btp.exe \(`C:\Users<your-user>`\).

4.  \(Optional\) If you have a proxy server configured in your environment, you need to specify its address and port as environment variable `HTTPS_PROXY` or `https_proxy` to access SAP BTP. For example, `HTTPS_PROXY=https://my-https-proxy:1234`.

    The specified proxy server is then used for HTTPS requests, unless overriden by the `NO_PROXY` or `no_proxy`, environment variables, which define a comma-separated list of hosts to be excluded from proxying.

5.  Run `btp` in your terminal. Note that you need read and write permissions in the target folder to run this executable.

6.  Log in to your global account with `btp login` or `btp login --sso`. The login flow is interactive and will prompt for all required information. Note that you need to confirm the btp CLI server url \(`https://cli.btp.cloud.sap/`\) and, if you have more than one, select your global account. For details, see [Log in](log-in-e241b30.md).

7.  Once you're logged in, familiarize yourself with the btp CLI, for example with [How to Work with the btp CLI](how-to-work-with-the-btp-cli-11d9f67.md), [Command Syntax of the btp CLI](command-syntax-of-the-btp-cli-69606f4.md), or simply by trying out a few commands, such as the following:

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

8.  If you’re going to work in a subaccount of this global account, consider setting the target to this subaccount using `btp target` and select the subaccount. See [Set a Target for Subsequent Commands with btp target](set-a-target-for-subsequent-commands-with-btp-target-720645a.md).

9.  To find out the current context, target, and version, use `btp`.


**Related Information**  


[How to Work with the btp CLI](how-to-work-with-the-btp-cli-11d9f67.md "Learn how to work with the SAP BTP command line interface (btp CLI). For example, how to log in, get help, and set a default context for commands.")

[Command Syntax of the btp CLI](command-syntax-of-the-btp-cli-69606f4.md "Each command consists of the base call btp followed by a verb (the action), a combination of group and object, and parameters.")

[Set a Target for Subsequent Commands with btp target](set-a-target-for-subsequent-commands-with-btp-target-720645a.md "Set the target for command calls to a subaccount, a directory, or a global account with the btp target command.")

[btp CLI Command Reference](https://help.sap.com/docs/BTP/btp-cli/intro.html)

