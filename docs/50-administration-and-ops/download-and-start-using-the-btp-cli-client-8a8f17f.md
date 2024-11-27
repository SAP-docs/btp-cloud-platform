<!-- loio8a8f17f5fd334fb583438edbd831d506 -->

# Download and Start Using the btp CLI Client

To use the SAP BTP command line interface \(btp CLI\), you need to download the client first.



<a name="loio8a8f17f5fd334fb583438edbd831d506__section_kl1_dcg_jdc"/>

## Context

Each client version is supported for at least one year and most of the updates to the btp CLI don't require a new client installation, but are made available through the btp CLI server so that you can use them in your installed version of the client. Regularly updating the client, however, will ensure that you don’t miss out on any new features or security updates.

Check out the [What's New for SAP Business Technology Platform](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?Component=SAP%20BTP%20Command%20Line%20Interface&locale=en-US&version=Cloud) page on SAP Help Portal \(filtered for *SAP BTP Command Line Interface*\) to stay informed about features, client releases, as well about client deprecations and discontinuations.

The client is available for 64-bit versions of the following operating systems:

-   Microsoft Windows \(amd64\)
-   Apple macOS \(amd64 and arm64\)
-   Linux \(amd64 and arm64\)

There are various ways of downloading the client for each operating system, as explained below.

**Related Information**  


[How to Work with the btp CLI](how-to-work-with-the-btp-cli-11d9f67.md "Learn how to work with the SAP BTP command line interface (btp CLI). For example, how to log in, get help, and set a default context for commands.")

[Command Syntax of the btp CLI](command-syntax-of-the-btp-cli-69606f4.md "Each command consists of the base call btp followed by a verb (the action), a combination of group and object, and parameters.")

[Set a Target for Subsequent Commands with btp target](set-a-target-for-subsequent-commands-with-btp-target-720645a.md "Set the target for command calls to a subaccount, a directory, or a global account with the btp target command.")

[btp CLI Command Reference](https://help.sap.com/docs/BTP/btp-cli/intro.html)

<a name="loio28a339f4145842cb88681af8ec66996c"/>

<!-- loio28a339f4145842cb88681af8ec66996c -->

## Microsoft Windows \(amd64\)



## Procedure

1.  You can get the btp CLI client by running the installation script or manually downloading it.

    -   Option 1: **Installation Script \(Windows PowerShell\)**

        When you run the installation script in Windows PowerShell, you will be guided through the installation process:

        ```
        Invoke-RestMethod 'https://cli.btp.cloud.sap/btpcli-install.ps1' | Invoke-Expression
        ```

        To uninstall the btp CLI:

        ```
        Invoke-RestMethod 'https://cli.btp.cloud.sap/btpcli-uninstall.ps1' | Invoke-Expression
        ```

    -   Option 2: **Manually install the latest Microsoft Windows \(amd64\) version**

        1.  Download the latest [Microsoft Windows client](https://tools.hana.ondemand.com/additional/btp-cli-windows-amd64-latest.tar.gz) from [SAP Development Tools](https://tools.hana.ondemand.com/#cloud-btpcli). If you prefer using the command line, use the curl command, which downloads and saves the latest client version to your computer and accepts the SAP Developer Agreement \(EULA\).

            ```
            curl -LJO https://tools.hana.ondemand.com/additional/btp-cli-windows-amd64-latest.tar.gz --cookie "eula_3_2_agreed=tools.hana.ondemand.com/developer-license-3_2.txt"
            ```

        2.  Extract the client from tar.gz archive.

            Use PowerShell or an external program, such as WinRar, to extract the tar.gz file. Tip: Once you've unpacked the executable file, enter `cmd` or `powershell` in the address bar of the folder. This opens the command prompt or PowerShell in this folder. Or proceed with the next step in order to enable calling `btp` from any location on your system.

        3.  Copy the client executable from the unpacked folder to a directory of your choice. We recommend the following, because it ensures that you can call `btp` system-wide, i.e., that it is in your PATH:

            `C:/Users/<your-user>`

            In the Windows search, enter `Environment Variable` and open the *System Properties*. On the *Advanced* tab, open *Environment Variables*. Under *User Variables*, open the *Path* entry and add the file location of the btp.exe \(`C:\Users<your-user>`\).

        4.  **Optional:** If you have a proxy server configured in your environment, you need to specify its address and port as environment variable `HTTPS_PROXY` or `https_proxy` to access SAP BTP. For example, `HTTPS_PROXY=https://my-https-proxy:1234`.

            The specified proxy server is then used for HTTPS requests, unless overridden by the NO\_PROXY or no\_proxy, environment variables, which define a comma-separated list of hosts to be excluded from proxying.



2.  Run `btp` in your terminal. Note that you need read and write permissions in the target folder to run this executable.

3.  Log into your global account with `btp login` or `btp login --sso`. The login flow is interactive and will prompt for all required information. Note that you need to confirm the btp CLI server \(`https://cli.btp.cloud.sap/`and, if you have more than one, select your global account. For details, see [Log in](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/e241b30195ff4d009dba3076e0ae8d27.html?locale=en-US&state=PRODUCTION&version=Cloud).

4.  Once you're logged in, familiarize yourself with the btp CLI, for example with [How to Work with the btp CLI](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/11d9f67d2c68485ca2f435b955d3b85b.html?locale=en-US&state=PRODUCTION&version=Cloud), [Command Syntax of the btp CLI](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/69606f42743f46c29fa72c04e8c18674.html?locale=en-US&state=PRODUCTION&version=Cloud), or simply by trying out a few commands, such as the following:

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
    > Use the command autocompletion feature in the btp CLI to save keystrokes when entering command actions, group-object combinations, and their parameters in the command line. For more information, see [Enable Command Autocompletion](enable-command-autocompletion-46355fa.md).

5.  If you're going to work in a subaccount of this global account, consider setting the target to this subaccount using `btp target` and select the subaccount. See [Set a Target for Subsequent Commands with btp target](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/720645a3ed3945bd8d97a670b948ac07.html?locale=en-US&state=PRODUCTION&version=Cloud).

6.  To view the current context, target, and version, use `btp`.


<a name="loio6c48b6dbd6f744778e4389f935a3e554"/>

<!-- loio6c48b6dbd6f744778e4389f935a3e554 -->

## Apple macOS \(amd64 and arm64\)



<a name="loio6c48b6dbd6f744778e4389f935a3e554__steps_pvc_nm5_ldc"/>

## Procedure

1.  You can get the btp CLI client by running the installation script or manually downloading it.

    -   Option 1: **Installation Script**

        When you run the installation script in your Apple macOS terminal, you will be guided through the installation process:

        ```
        curl https://cli.btp.cloud.sap/btpcli-install.sh | zsh
        ```

        To uninstall the btp CLI:

        ```
        curl https://cli.btp.cloud.sap/btpcli-uninstall.sh | zsh
        ```

    -   Option 2: **Manually install the latest Apple macOS \(amd64 and arm64\) version**

        1.  Download the latest Apple macOS client \([amd64](https://tools.hana.ondemand.com/additional/btp-cli-darwin-amd64-latest.tar.gz) or [arm64](https://tools.hana.ondemand.com/additional/btp-cli-darwin-arm64-latest.tar.gz)\) from [SAP Development Tools](https://tools.hana.ondemand.com/#cloud-btpcli). If you prefer using the command line, use the curl command, which downloads and saves the latest client version to your computer and accepts the SAP Developer Agreement \(EULA\).

            For Apple macOS amd64:

            ```
            curl -LJO https://tools.hana.ondemand.com/additional/btp-cli-darwin-amd64-latest.tar.gz --cookie "eula_3_2_agreed=tools.hana.ondemand.com/developer-license-3_2.txt"
            ```

            For Apple macOS arm64:

            ```
            curl -LJO https://tools.hana.ondemand.com/additional/btp-cli-darwin-arm64-latest.tar.gz --cookie "eula_3_2_agreed=tools.hana.ondemand.com/developer-license-3_2.txt"
            ```

        2.  Extract the client from tar.gz archive.

            Open the tar.gz file by double-clicking it.

        3.  Copy the client executable from the unpacked folder to a directory of your choice. We recommend the following, because it ensures that you can call `btp` system-wide, i.e., that it is in your PATH:

            `/user/local/bin`

        4.  **Optional:** If you have a proxy server configured in your environment, you need to specify its address and port as environment variable `HTTPS_PROXY` or `https_proxy` to access SAP BTP. For example, `HTTPS_PROXY=https://my-https-proxy:1234`.

            The specified proxy server is then used for HTTPS requests, unless overridden by the NO\_PROXY or no\_proxy, environment variables, which define a comma-separated list of hosts to be excluded from proxying.



2.  Run `btp` in your terminal. Note that you need read and write permissions in the target folder to run this executable.

3.  Log into your global account with `btp login` or `btp login --sso`. The login flow is interactive and will prompt for all required information. Note that you need to confirm the btp CLI server \(`https://cli.btp.cloud.sap/`and, if you have more than one, select your global account. For details, see [Log in](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/e241b30195ff4d009dba3076e0ae8d27.html?locale=en-US&state=PRODUCTION&version=Cloud).

4.  Once you're logged in, familiarize yourself with the btp CLI, for example with [How to Work with the btp CLI](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/11d9f67d2c68485ca2f435b955d3b85b.html?locale=en-US&state=PRODUCTION&version=Cloud), [Command Syntax of the btp CLI](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/69606f42743f46c29fa72c04e8c18674.html?locale=en-US&state=PRODUCTION&version=Cloud), or simply by trying out a few commands, such as the following:

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
    > Use the command autocompletion feature in the btp CLI to save keystrokes when entering command actions, group-object combinations, and their parameters in the command line. For more information, see [Enable Command Autocompletion](enable-command-autocompletion-46355fa.md).

5.  If you're going to work in a subaccount of this global account, consider setting the target to this subaccount using `btp target` and select the subaccount. See [Set a Target for Subsequent Commands with btp target](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/720645a3ed3945bd8d97a670b948ac07.html?locale=en-US&state=PRODUCTION&version=Cloud).

6.  To view the current context, target, and version, use `btp`.


<a name="loioe1caa5f29fb340e797cc13383451dcf9"/>

<!-- loioe1caa5f29fb340e797cc13383451dcf9 -->

## Linux \(amd64 and arm64\)



<a name="loioe1caa5f29fb340e797cc13383451dcf9__steps_pvc_nm5_ldc"/>

## Procedure

1.  You can get the btp CLI client by running the installation script or manually downloading it.

    -   Option 1: **Installation Script**

        When you run the installation script in your Linux terminal, you will be guided through the installation process:

        ```
        curl https://cli.btp.cloud.sap/btpcli-install.sh | bash
        ```

        To uninstall the btp CLI:

        ```
        curl https://cli.btp.cloud.sap/btpcli-uninstall.sh | bash
        ```

    -   Option 2: **Manually install the latest Linux \(amd64 and arm64\) version**

        1.  Download the latest Linux client \([amd64](https://tools.hana.ondemand.com/additional/btp-cli-linux-amd64-latest.tar.gz) or [arm64](https://tools.hana.ondemand.com/additional/btp-cli-linux-arm64-latest.tar.gz)\) from [SAP Development Tools](https://tools.hana.ondemand.com/#cloud-btpcli). If you prefer using the command line, use the curl command, which downloads and saves the latest client version to your computer and accepts the SAP Developer Agreement \(EULA\).

            For Linux amd64:

            ```
            curl -LJO https://tools.hana.ondemand.com/additional/btp-cli-linux-amd64-latest.tar.gz --cookie "eula_3_2_agreed=tools.hana.ondemand.com/developer-license-3_2.txt"
            ```

            For Linux arm64:

            ```
            curl -LJO https://tools.hana.ondemand.com/additional/btp-cli-linux-arm64-latest.tar.gz --cookie "eula_3_2_agreed=tools.hana.ondemand.com/developer-license-3_2.txt"
            ```

        2.  Extract the client from tar.gz archive.

            Use the terminal to open the tar.gz file with `tar -xzf btp-cli-linus-amd64-latest.tar.gz`

        3.  Copy the client executable from the unpacked folder to a directory of your choice. We recommend the following, because it ensures that you can call `btp` system-wide, i.e., that it is in your PATH:

            `/user/local/bin`

        4.  **Optional:** If you have a proxy server configured in your environment, you need to specify its address and port as environment variable `HTTPS_PROXY` or `https_proxy` to access SAP BTP. For example, `HTTPS_PROXY=https://my-https-proxy:1234`.

            The specified proxy server is then used for HTTPS requests, unless overridden by the NO\_PROXY or no\_proxy, environment variables, which define a comma-separated list of hosts to be excluded from proxying.



2.  Run `btp` in your terminal. Note that you need read and write permissions in the target folder to run this executable.

3.  Log into your global account with `btp login` or `btp login --sso`. The login flow is interactive and will prompt for all required information. Note that you need to confirm the btp CLI server \(`https://cli.btp.cloud.sap/`and, if you have more than one, select your global account. For details, see [Log in](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/e241b30195ff4d009dba3076e0ae8d27.html?locale=en-US&state=PRODUCTION&version=Cloud).

4.  Once you're logged in, familiarize yourself with the btp CLI, for example with [How to Work with the btp CLI](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/11d9f67d2c68485ca2f435b955d3b85b.html?locale=en-US&state=PRODUCTION&version=Cloud), [Command Syntax of the btp CLI](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/69606f42743f46c29fa72c04e8c18674.html?locale=en-US&state=PRODUCTION&version=Cloud), or simply by trying out a few commands, such as the following:

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
    > Use the command autocompletion feature in the btp CLI to save keystrokes when entering command actions, group-object combinations, and their parameters in the command line. For more information, see [Enable Command Autocompletion](enable-command-autocompletion-46355fa.md).

5.  If you're going to work in a subaccount of this global account, consider setting the target to this subaccount using `btp target` and select the subaccount. See [Set a Target for Subsequent Commands with btp target](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/720645a3ed3945bd8d97a670b948ac07.html?locale=en-US&state=PRODUCTION&version=Cloud).

6.  To view the current context, target, and version, use `btp`.


<a name="loioe92aa7859bc94a07a764f49c0437ead3"/>

<!-- loioe92aa7859bc94a07a764f49c0437ead3 -->

## Get Updates

Updating the btp CLI client is essentially replacing the old executable file with a newer version.



<a name="loioe92aa7859bc94a07a764f49c0437ead3__context_u1f_2kd_yjb"/>

## Context

Each btp CLI client version is supported for at least a year after its release, but we recommend to regularly update the client. This way, you won't miss any new features or security updates. The [What's New for SAP Business Technology Platform](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?Component=SAP%20BTP%20Command%20Line%20Interface&locale=en-US&version=Cloud) page on SAP Help Portal announces new features and informs you if you need a client update to use them. If your client version is deprecated, an update hint is displayed in the client as well.

To find out the version of the CLI client you are using, run `btp --info` or simply `btp`.



## Procedure

1.  Get the latest version either by re-running the installation script or downloading the client manually.

2.  Extract the client file \(for example: `btp.exe`\) and replace the old file with this new one.

3.  Work with the btp CLI as usual and enjoy the new features.


**Related Information**  


[Log in](log-in-e241b30.md "Log in with the btp CLI is on global account level.")

[Commands in the btp CLI](commands-in-the-btp-cli-a03a555.md "Find a full reference of all btp CLI commands and their parameters here: btp CLI Command Reference.")

