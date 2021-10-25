<!-- loio9d29c387473a4627b127c5b8d09ef234 -->

# Extending the Application Router

Configure application-specific extensions for the application router.



Instead of starting the application router directly, you can configure your XS advanced application to use its own start script. You can also use the application router as a regular Node.js package.

> ### Sample Code:  
> ```
> var approuter = require('approuter');
> 
> var ar = approuter();
> ar.start();
> ```



## Custom Middleware Injection

The application router uses the connect framework, for more information, see *Connect framework* in the *Related Links* below. You can reuse all injected “connect” middleware within the application router, for example, directly in the application start script:

> ### Sample Code:  
> ```
> var approuter = require('approuter');
> 
> var ar = approuter();
> 
> ar.beforeRequestHandler.use('/my-ext', function myMiddleware(req, res, next) {
>   res.end('Request handled by my extension!');
> });
> ar.start();
> ```

> ### Tip:  
> To facilitate troubleshooting, always provide a name for your custom middleware.

The `path` argument is optional. You can also chain `use` calls.

> ### Sample Code:  
> ```
> var approuter = require('approuter');
> var morgan = require('morgan');
> 
> var ar = approuter();
> 
> ar.beforeRequestHandler
>   .use(morgan('combined'))
>   .use('/my-ext', function myMiddleware(req, res, next) {
>     res.end('Request handled by my extension!');
>   });
> ar.start();
> ```

The application router defines the following slots where you can insert custom middleware:

-   `first` - right after the connect application is created, and before any application router middleware. At this point security checks are not performed yet.

    > ### Tip:  
    > This is good place for infrastructure logic, for example, logging and monitoring.

-   `beforeRequestHandler` - before standard application router request handling, that is static resource serving or forwarding to destinations.

    > ### Tip:  
    > This is a good place to handle custom REST API requests.

-   `beforeErrorHandler` - before standard application router error handling.

    > ### Tip:  
    > This is a good place to capture or customize error handling.


If your middleware does not complete the request processing, call `next` to return control to the application router middleware, as illustrated in the following example:

> ### Sample Code:  
> ```
> ar.beforeRequestHandler.use('/my-ext', function myMiddleware(req, res, next) {
>   res.setHeader('x-my-ext', 'passed');
>   next();
> });
> ```



## Application Router Extensions

An extension is defined by an object with the following properties:

-   `insertMiddleware` - describes the middleware provided by this extension

    -   `first`, `beforeRequestHandler`, and `beforeErrorHandler`

        An array of middleware, where each one can be either of the following elements:

        -   A middleware function \(invoked on all requests\)

        -   An object with the following properties:

            -   `path`

                Handle requests only for this path

            -   `handler`

                The middleware function to invoke





> ### Sample Code:  
> Example Approuter Extension Configuration \(`my-ext.js`\)
> 
> ```
> module.exports = {
>   insertMiddleware: {
>     first: [
>       function logRequest(req, res, next) {
>         console.log('Got request %s %s', req.method, req.url);
>       }
>     ],
>     beforeRequestHandler: [
>       {
>         path: '/my-ext',
>         handler: function myMiddleware(req, res, next) {
>           res.end('Request handled by my extension!');
>         }
>       }
>     ]
>   }
> };
> ```

The extension configuration can be referenced in the corresponding application's start script, as illustrated in the following example:

> ### Sample Code:  
> ```
> var approuter = require('approuter');
> 
> var ar = approuter();
> ar.start({
>   extensions: [
>     require('./my-ext.js')
>   ]
> });
> ```



## Customize Command Line

By default the application router handles its command-line parameters, but that can be customized as well.

An *<approuter\>* instance provides the property `cmdParser` that is a commander instance. It is configured with the standard application router command line options. You can add custom options like this:

> ### Sample Code:  
> ```
> var approuter = require('approuter');
> 
> var ar = approuter();
> 
> var params = ar.cmdParser
>   // add here custom command line options if needed
>   .option('-d, --dummy', 'A dummy option')
>   .parse(process.argv);
> 
> console.log('Dummy option:', params.dummy);
> ```

To disable the handling of command-line options in the application router, reset the `ar.cmdParser` property to “`false`”, as illustrated in the following example:

```
ar.cmdParser = false;
```

**Related Information**  


[Middleware Connect Framework](https://github.com/senchalabs/connect)

[Extension API of the Application Router](Extension_API_of_the_Application_Router_a36f409.md "A detailed list of the features and functions provided by the application router extension API.")

