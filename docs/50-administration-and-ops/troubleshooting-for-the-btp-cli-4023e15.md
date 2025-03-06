<!-- loio4023e1504ebc4a00a5108b8f716fe9a3 -->

# Troubleshooting for the btp CLI

Troubleshooting and support information for the btp CLI.



<a name="loio4023e1504ebc4a00a5108b8f716fe9a3__section_dv5_kb1_ckb"/>

## Make sure that you are using a recent version of the btp CLI client

We recommend checking for updates of the client on a regular basis. Most new functionality is added via the CLI server, so no update from your side is required. But if new functionality is added to the client, the only way to get it is by downloading and installing the latest version.

Run the command `btp` or `btp --info` to see which version of the client you are using. To get the latest client, you can run the [installation script](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/8a8f17f5fd334fb583438edbd831d506.html?locale=en-US&state=PRODUCTION&version=Cloud) for your operating system. Alternatively, you can check on our [download page](https://tools.hana.ondemand.com/#cloud-cpcli) for the current version and manually install the latest client.

Use `btp --help` to display an overview of all commands. If new commands are available but cannot be used with your client version, these commands are marked with a notice to update your client. If you run such a command, you get an error message pointing you to the client version that you need.



<a name="loio4023e1504ebc4a00a5108b8f716fe9a3__section_b25_g3c_xlb"/>

## I can't log on

To log on, we recommend to run `btp login --sso` or `btp login` without parameters. Then confirm the server URL that is proposed by the CLI and provide your credentials when you are prompted. After successful authentication, the btp CLI will log you into your global account, or, if you have more than one, will show all available global accounts for you to select the one you need.

To log on with SAP Universal ID, you need to use the `--sso` parameter. Otherwise log on with the password associated with your account \(S-user or P-user\) in the default identity provider, SAP ID service. If you've forgotten this password and this user is associated with your SAP Universal ID user, reset your password.

For more information, see SAP Note [3085908](https://me.sap.com/notes/3085908) and [Log in with Single Sign-On](log-in-with-single-sign-on-b2a56a8.md).



<a name="loio4023e1504ebc4a00a5108b8f716fe9a3__section_p1h_yzh_42c"/>

## I'm getting an error message about connecting to the server

If you get an error message about connecting to the server, you should update your root CA or install the custom CA for the login URL you used. The btp CLI uses system defaults to locate the installed CA certificates. You should therefore follow the standard instructions for your operating system.



<a name="loio4023e1504ebc4a00a5108b8f716fe9a3__section_tpf_hyh_xlb"/>

## I'd like to setup a global account with the command line

If you don't know how to get started, you might want to have a look at the appropriate workflow: [Setting Up a Trial Account From the Command Line](../20-getting-started/setting-up-a-trial-account-from-the-command-line-a21360f.md) or [Setting Up a Global Account via the Command Line](../20-getting-started/setting-up-a-global-account-via-the-command-line-accd5b2.md).



<a name="loio4023e1504ebc4a00a5108b8f716fe9a3__section_csr_4s1_ckb"/>

## I'd like to see a more detailed output \(verbose mode\)

If you get an error message that is not helpful enough, or if you want to find out more about what exactly happened after you ran a command, use the `btp --verbose` option with your command and run it again. The btp CLI will try to execute the command again, but also print information about each step of the command execution. This might help you understand what exactly went wrong and provide hints for you to solve the issue. If you need to create a support request, providing this information helps us analyze the error and provide a solution more quickly.

Here is an example of the `btp list security/role-collection` command call without the option:

> ### Sample Code:  
> ```
> btp list security/role-collection
> name                         	description
> Global Account Administrator 	Administrative access to the global account
> Global Account Viewer        	Read-only access to the global account
> 
> OK
> 
> ```

If you use `btp --verbose list security/role-collection`, the output is much more lengthy. It contains information such as client version and the current context, the correlation ID, and request and response details. This output may include sensitive information, so we recommend to use the verbose mode only for troubleshooting, not as default, and only on your local machine.

> ### Caution:  
> The `--verbose` option prints input data that you pass as parameters through files. For example, if you pass a .json file as a parameter without the `--verbose` option, its content is sent directly to the backend service to be processed. If you use the `--verbose` option, the btp CLI prints the content of the file to the terminal. If there is sensitive information in such a file, the btp CLI cannot filter it out, as it doesn't understand its semantics.
> 
> Use the verbose output only if you can control the output of your terminal, i.e. only locally. It should not be used in production or shared environments, where logs may be persisted or even transported out of the system.

> ### Sample Code:  
> ```
> btp --verbose list security/role-collection
> 2019/12/18 10:35:21.309235 main.go:34: Support trace activated.
> 2019/12/18 10:35:21.309284 main.go:35: Client version 1.x.x running with command line: --verbose list security/role-collection
> 2019/12/18 10:35:21.309349 clifiles.go:65: Config file path was set to /Users/my-user/Library/Caches/.btp/config.json
> 2019/12/18 10:35:21.309386 login.go:138: Reading configuration from &{/Users/my-user/Library/Caches/.btp config.json commands.json}
> 2019/12/18 10:35:21.309578 main.go:60: CLI server URL:            http://localhost:8080
> 2019/12/18 10:35:21.309591 main.go:60: Global account subdomain:  my-ga-subdomain
> 2019/12/18 10:35:21.309594 main.go:60: Subaccount:                not set
> 2019/12/18 10:35:21.309597 main.go:60: Configuration file:        /Users/my-user/Library/Caches/.btp/config.json
> 2019/12/18 10:35:21.309603 login.go:138: Reading configuration from &{/Users/my-user/Library/Caches/.btp config.json commands.json}
> 2019/12/18 10:35:21.309663 main.go:68: Successfully loaded login config.
> 2019/12/18 10:35:21.311758 protocol.go:41: Loading command metadata from http://localhost:8080/commandMetadata/v-1
> 2019/12/18 10:35:21.311860 protocol.go:248: Adding correlation ID 1234abcde-ab12-12ab-34cd-123456abcdef to request http://localhost:8080/commandMetadata/v-1
> 2019/12/18 10:35:21.319441 protocol.go:53: Received response 200 from request http://localhost:8080/commandMetadata/v-1
> 2019/12/18 10:35:21.322441 protocol.go:161: Executing command list security/role-collection with parameters map[subaccount:{0 }]
> 2019/12/18 10:35:21.322622 protocol.go:205: Sending request:
> {POST http://localhost:8080/command/v-1/security/role-collection?list HTTP/1.1 1 1 map[Content-Type:[application/json;charset=UTF-8] X-Cpcli-Subdomain:[my-ga-subdomain]] {{"paramValues":{"subaccount":null}}} 0x12c6380 35 [] false localhost:8080 map[] map[] <nil> map[]   <nil> <nil> <nil> 0xc0000ae070}
> to http://localhost:8080/command/v-1/security/role-collection?list
> 2019/12/18 10:35:21.322642 protocol.go:248: Adding correlation ID 1234abcde-ab12-12ab-34cd-123456abcdef to request http://localhost:8080/command/v-1/security/role-collection?list
> 2019/12/18 10:35:24.683689 protocol.go:214: Received response 200 from request http://localhost:8080/command/v-1/security/role-collection?list
> 2019/12/18 10:35:24.690916 main.go:196: Getting response mapping for command result code 200
> 2019/12/18 10:35:24.690943 main.go:198: Response mapping: {[200] ok {table  [name description]}}
> name                         description
> Global Account Administrator Administrative access to the global account
> Global Account Viewer        Read-only access to the global account
> 
> OK
> 
> ```



<a name="loio4023e1504ebc4a00a5108b8f716fe9a3__section_q5m_151_ckb"/>

## I need support

Use component `BC-CP-TOOLS-CLI` to contact support.

If a correlation ID is printed with your error message, please provide it with your support ticket. The correlation ID is created for each command execution, and is passed with all of its steps. It allows the identification of all log messages related to a command execution.

See [Getting Support](../70-getting-support/getting-support-5dd7398.md).

