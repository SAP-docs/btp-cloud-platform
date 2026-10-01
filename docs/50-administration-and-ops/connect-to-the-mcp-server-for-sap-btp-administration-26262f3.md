<!-- loio26262f3937c14283a21c36a1cafc7039 -->

# Connect to the MCP Server for SAP BTP Administration

Register the MCP Server for SAP BTP Administration in your AI client to start managing your BTP account using natural language.



<a name="loio26262f3937c14283a21c36a1cafc7039__prereqs"/>

## Prerequisites

Ensure that you meet the following requirements before connecting:

-   You have an MCP compatible AI client installed. Examples of supported clients include Claude Code, GitHub Copilot in VS Code, and OpenCode.
-   You have access to an SAP BTP global account.
-   You have determined which authentication mode applies to your setup:


    <table>
    <tr>
    <th valign="top">

    Authentication mode
    
    </th>
    <th valign="top">

    When to use
    
    </th>
    <th valign="top">

    What you need
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Single Sign-On \(SSO\)
    
    </td>
    <td valign="top">
    
    Your BTP platform user comes from the Default Identity Provider \(`accounts.sap.com`\).
    
    </td>
    <td valign="top">
    
    An SAP user account and browser access for the one-time login flow.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Direct Connection
    
    </td>
    <td valign="top">
    
    Your BTP platform user comes from a custom identity provider configured as a platform trust in your global account.
    
    </td>
    <td valign="top">
    
    Your IAS username and password \(Base64-encoded\), and your IAS tenant subdomain. If your IAS tenant delegates login to a corporate identity provider \(for example, PingID or Microsoft Entra ID\), use your IAS credentials.
    
    </td>
    </tr>
    </table>
    

> ### Note:  
> After the initial login, your session is maintained automatically:
> 
> -   *Access tokens* expire after 30 minutes.
> -   *Refresh tokens* are valid for 1 day and rotate on every use.
> 
> Your MCP client renews access tokens silently in the background.
> 
> Your session ends if the server goes unused for a full day, or if you explicitly log out of your SAP account from the browser \(SAP Identity Service at `accounts.sap.com`\). In either case, your client opens the browser login again automatically.



<a name="loio26262f3937c14283a21c36a1cafc7039__context"/>

## Context

The MCP Server for SAP BTP Administration is available at the following endpoint:


<table>
<tr>
<th valign="top">

Authentication mode

</th>
<th valign="top">

URL

</th>
</tr>
<tr>
<td valign="top">

Single Sign-On

</td>
<td valign="top">

`https://sso.mcp.btp.cloud.sap/mcp`

</td>
</tr>
<tr>
<td valign="top">

Direct Connection

</td>
<td valign="top">

`https://proxy.c-769d49e.kyma.ondemand.com/mcp`

</td>
</tr>
</table>

For SSO, you must also provide the OAuth client ID when registering the server: `e789ba01-5612-47ee-bfe7-79e26411c1ca`

> ### Caution:  
> The MCP Server operates with the full scope of your SAP user identity. If your trial account is registered under the same email address as your productive accounts, the server will have access to all global accounts associated with that identity. To restrict access to a trial account only, register it under a separate email address.



## Procedure

Follow the instructions for your AI client.


<table>
<tr>
<th valign="top">

AI client

</th>
<th valign="top">

Instructions

</th>
</tr>
<tr>
<td valign="top">

**Claude Code**

</td>
<td valign="top">

**Single Sign-On**

1.  Open a terminal and run the following command:

    ```
    claude mcp add --transport http BTP-Administration \
      "https://sso.mcp.btp.cloud.sap/mcp" \
      --client-id e789ba01-5612-47ee-bfe7-79e26411c1ca
    ```

    You only need to run this command once. The server remains registered across sessions.

2.  Start Claude Code: `claude`
3.  Type `/mcp` at the prompt and select the server you registered.
4.  Complete the SAP login in the browser that opens, then return to your terminal.

**Direct Connection**

1.  Compute the Base64 encoding of your IAS credentials in the format `<username>:<password>` and set it as an environment variable along with your IAS tenant subdomain.

    macOS and Linux:

    ```
    export BTP_CREDENTIALS=$(echo -n "<your-username>:<your-password>" | base64)
    export BTP_ORIGIN="<your-ias-tenant-subdomain>"
    ```

    Windows \(PowerShell\):

    ```
    $Env:BTP_CREDENTIALS = [Convert]::ToBase64String([Text.Encoding]::UTF8.GetBytes('<your-username>:<your-password>'))
    $Env:BTP_ORIGIN = '<your-ias-tenant-subdomain>'
    ```

2.  Register the server:

    ```
    claude mcp add --transport http BTP-Administration \
      "https://proxy.c-769d49e.kyma.ondemand.com/mcp" \
      --header 'Authorization: Basic ${BTP_CREDENTIALS}' \
      --header 'X-Platform-Origin: ${BTP_ORIGIN}'
    ```

3.  Start Claude Code: `claude`



</td>
</tr>
<tr>
<td valign="top">

**GitHub Copilot in VS Code**

</td>
<td valign="top">

**Single Sign-On**

1.  Open or create `.vscode/mcp.json` in your project and add the following entry:

    ```
    {
      "servers": {
        "BTP Administration": {
          "type": "streamableHttp",
          "url": "https://sso.mcp.btp.cloud.sap/mcp"
        }
      }
    }
    ```

2.  When VS Code prompts for the OAuth client ID, enter `e789ba01-5612-47ee-bfe7-79e26411c1ca`. VS Code stores this value and will not ask again.
3.  Complete the SAP login in the browser that opens, then return to VS Code.

**Direct Connection**

1.  Before configuring VS Code, compute the Base64 encoding of your IAS credentials in the format `<username>:<password>`.

    macOS and Linux:

    ```
    echo -n "<your-username>:<your-password>" | base64
    ```

    Windows \(PowerShell\):

    ```
    [Convert]::ToBase64String([Text.Encoding]::UTF8.GetBytes('<your-username>:<your-password>'))
    ```

    Copy the output — you will enter it in the next step.

2.  Open or create `.vscode/mcp.json` and add the following. VS Code prompts for credentials once per session and does not store them on disk.

    ```
    {
      "inputs": [
        {
          "id": "btp-credentials",
          "type": "promptString",
          "description": "Base64-encoded BTP credentials (<username>:<password>)",
          "password": true
        },
        {
          "id": "btp-origin",
          "type": "promptString",
          "description": "IAS tenant subdomain"
        }
      ],
      "servers": {
        "BTP Administration": {
          "type": "streamableHttp",
          "url": "https://proxy.c-769d49e.kyma.ondemand.com/mcp",
          "headers": {
            "Authorization": "Basic ${input:btp-credentials}",
            "X-Platform-Origin": "${input:btp-origin}"
          }
        }
      }
    }
    ```




</td>
</tr>
<tr>
<td valign="top">

**OpenCode**

</td>
<td valign="top">

**Single Sign-On**

1.  Open your `opencode.json` configuration file and add the following entry under the `mcp` key:

    ```
    {
      "mcp": {
        "BTP Administration": {
          "type": "remote",
          "url": "https://sso.mcp.btp.cloud.sap/mcp",
          "oauth": {
            "clientId": "e789ba01-5612-47ee-bfe7-79e26411c1ca"
          }
        }
      }
    }
    ```

2.  Start OpenCode. Complete the SAP login in the browser that opens, then return to OpenCode.

**Direct Connection**

1.  Compute the Base64 encoding of your IAS credentials in the format `<username>:<password>` and set it as an environment variable along with your IAS tenant subdomain.

    macOS and Linux:

    ```
    export BTP_CREDENTIALS=$(echo -n "<your-username>:<your-password>" | base64)
    export BTP_ORIGIN="<your-ias-tenant-subdomain>"
    ```

    Windows \(PowerShell\):

    ```
    $Env:BTP_CREDENTIALS = [Convert]::ToBase64String([Text.Encoding]::UTF8.GetBytes('<your-username>:<your-password>'))
    $Env:BTP_ORIGIN = '<your-ias-tenant-subdomain>'
    ```

2.  Add the following to your `opencode.json`:

    ```
    {
      "mcp": {
        "BTP Administration": {
          "type": "remote",
          "url": "https://proxy.c-769d49e.kyma.ondemand.com/mcp",
          "headers": {
            "Authorization": "Basic {env:BTP_CREDENTIALS}",
            "X-Platform-Origin": "{env:BTP_ORIGIN}"
          }
        }
      }
    }
    ```




</td>
</tr>
</table>



<a name="loio26262f3937c14283a21c36a1cafc7039__result"/>

## Results

Your AI client is now connected to the MCP Server for SAP BTP Administration and can invoke BTP administration operations on your behalf.



<a name="loio26262f3937c14283a21c36a1cafc7039__postreq"/>

## Next Steps

If you encounter errors during or after connecting, see [Troubleshooting the MCP Server for SAP BTP Administration](troubleshooting-the-mcp-server-for-sap-btp-administration-6237892.md).

**Related Information**  


[Account Administration Using MCP Servers](account-administration-using-mcp-servers-2d167cb.md "Use the MCP Server for SAP BTP Administration to manage your SAP BTP account structure using natural language through a compatible AI assistant.")

