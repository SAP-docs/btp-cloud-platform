<!-- loioa36f409dac7d472cb4a10cd884e35012 -->

# Extension API of the Application Router

A detailed list of the features and functions provided by the application router extension API.



The application router extension API enables you to create new instances of the application router, manage the approuter instance, and insert middleware using the Node.js “connect” framework. This section contains detailed information about the following areas:

-   Approuter Extension API Reference

-   Middleware Slot




<a name="loioa36f409dac7d472cb4a10cd884e35012__section_c3y_tjh_wx"/>

## Approuter Extension API Reference

The application router uses the “Connect” framework for the insertion of middleware components. You can reuse all connect middleware within the application router directly.

**Approuter Extension API Functions**


<table>
<tr>
<td valign="top">

`approuter()` 



</td>
<td valign="top">

Creates a new instance of the application router



</td>
</tr>
<tr>
<td valign="top">

`first` 



</td>
<td valign="top">

Defines a “middleware slot” \(a slot for the insertion of middleware\) immediately after the `connect` application is created, and before any application router middleware

> ### Tip:  
> This is a good place to insert infrastructure logic, for example, logging and monitoring.



</td>
</tr>
<tr>
<td valign="top">

`beforeRequestHandler` 



</td>
<td valign="top">

Defines a “middleware slot” before the standard application router request handling, that is; static resource serving or forwarding to destinations.

> ### Tip:  
> This is a good place to handle custom REST API requests.



</td>
</tr>
<tr>
<td valign="top">

`beforeErrorHandler` 



</td>
<td valign="top">

Defines a “middleware slot” before the standard application router error handling

> ### Tip:  
> This is a good place to capture or customize error handling.



</td>
</tr>
<tr>
<td valign="top">

`start(options, callback)` 



</td>
<td valign="top">

Starts the application router with the given options.

-   `options` this argument is optional. If provided, it should be an object which can have any of the following properties:

    -   `port` - a TCP port the application router will listen to \(string, optional\)
    -   `workingDir` - the working directory for the application router, should contain the `xs-app.json` file \(string, optional\)
    -   `extensions` - an array of extensions, each one is an object as defined in Application Router Extensions \(optional\)
    -   `xsappConfig` - An object representing the content which is usually put in `xs-app.json` file. If this property is present it will take precedence over the content of `xs-app.json`.

-   `callback` - optional function with signature `callback(err)`. It is invoked when the application router has started or an error has occurred. If not provided and an error occurs \(for example the port is busy\), the application will abort.




</td>
</tr>
<tr>
<td valign="top">

`close(callback)` 



</td>
<td valign="top">

Stops the application router.

-   `callback` - optional function with signature `callback(err)`. It is invoked when the application router has stopped or an error has occurred.




</td>
</tr>
</table>



<a name="loioa36f409dac7d472cb4a10cd884e35012__section_ijc_vmh_wx"/>

## Middleware Slot

Manage the insertion of middleware slots with the application router.


<table>
<tr>
<td valign="top">

`use(path, handler)` 



</td>
<td valign="top">

Inserts a request handling middleware in the current slot.

-   `path` - handle only requests starting with this path \(string, optional\)

-   `handler` - a middleware function to invoke \(function, mandatory\)


Returns `this` for chaining.



</td>
</tr>
</table>

**Related Information**  


[Middleware Connect Framework](https://github.com/senchalabs/connect)

[Extending the Application Router](extending-the-application-router-9d29c38.md "Configure application-specific extensions for the application router.")

