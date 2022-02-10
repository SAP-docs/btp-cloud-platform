<!-- loio4f1fe8dd2739467cb7bcab63f918b8dc -->

# Migrating from sapcp to btp

The executable file was renamed from sapcp to btp, which makes it necessary to update all scripts to call btp instead of sapcp.



## Context

From version 1.32.0 to version 2.0.0, the executable file was renamed from**sapcp** to **btp**. All commands remain compatible, but all scripts must be updated to call btp instead of sapcp. A new configuration file is created for you automatically.

The sapcp client version 1.32.0 will be supported until September 2021.



## Procedure

1.  Download the latest btp CLI client for your operating system from [SAP Development Tools](https://tools.hana.ondemand.com/#cloud-btpcli).

2.  Update your scripts to call btp.

3.  Open `btp` in a terminal session.

    Your sapcp configration file \(`config.json`\) is carried over into a new btp configuration folder in your user data directory:

    -   Microsoft Windows: <code>C:\Users\<i class="varname">&lt;username&gt;</i>\AppData\Local\SAP\btp</code>

    -   Apple macOS / Linux: `$HOME/.btp`


    The old sapcp configuration folder in the same directory is kept, so you can still use the sapcp client. If you no longer need it, you can delete the folder.

4.  If you want to use command autocompletion, you can enable it with <code>btp enable autocomplete <i class="varname">&lt;SHELL&gt;</i></code>.


**Related Information**  


[Specify the Location of the Configuration File](specify-the-location-of-the-configuration-file-e57288d.md "You can change the location of the configuration file by using the --config option or the environment variable.")

[Enable Command Autocompletion](enable-command-autocompletion-46355fa.md "Use command autocompletion to save keystrokes when entering command actions, group-object combinations, and their parameters in the SAP BTP command line interface (btp CLI).")

[Command Syntax of the btp CLI](command-syntax-of-the-btp-cli-69606f4.md "Each command consists of the base call btp followed by a verb (the action), a combination of group and object, and parameters.")

