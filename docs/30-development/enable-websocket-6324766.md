<!-- loio6324766470104b60a0f81d036d1d233d -->

# Enable WebSocket

You can enable WebSocket extensions to build ABAP applications that update their data live and do not require a manual refresh. For more information, refer to [WebSocket documentation](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/target-system-configuration?version=Cloud#loioab6eac92978f469e9eabe3d477ca2411__web)\). Enable WebSocket extensions to use **Event-Driven RAP Side Effects** \(check [Event-Driven RAP Side Effects](https://help.sap.com/docs/abap-cloud/abap-rap/using-side-effect-events?locale=en-US)\) and **Collaborative Draft Handling** \(check [Collabroative Draft Handling](https://help.sap.com/docs/abap-cloud/abap-rap/collaborative-draft?locale=en-US)\).

To enable WebSocket extensions, you need to configure your application router and enable the environment variable *HANDLE\_WEBSOCKET\_EXT* \(check [Routing Configuration File](https://help.sap.com/docs/btp/sap-business-technology-platform/routing-configuration-file?locale=en-US&version=Cloud); check [Environment Variables](https://help.sap.com/docs/btp/sap-business-technology-platform/environment-variables?version=Cloud)\).

Here's how you do it.

1.  In the `mta.yaml` file in your ABAP Solution Repository, configure the environment variable *HANDLE\_WEBSOCKET\_EXT*.

    By default, the environment variable *HANDLE\_WEBSOCKET\_EXT* is not configured and WebSocket extensions disabled: `HANDLE_WEBSOCKET_EXT=false`.

    To enable WebSocket extensions, set the environment variable *HANDLE\_WEBSOCKET\_EXT* to async: `HANDLE_WEBSOCKET_EXT=async`

    > ### Sample Code:  
    > ```
    > HANDLE_WEBSOCKET_EXT: async
    > ```

2.  Adjust the routing configuration in the `xs-app.json` file \(check [websockets](https://help.sap.com/docs/btp/sap-business-technology-platform/websockets?locale=en-US&version=Cloud)\).

    > ### Sample Code:  
    > ```
    > {
    >   "websockets": {
    >     "enabled": true
    >   }
    > }
    > ```

3.  Redeploy your solution.

