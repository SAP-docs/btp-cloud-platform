<!-- loio582d4056ea7c44a7a315e37ca2a5a64b -->

# Context Root Redirect

The SAP Java Buildpack provides a context root redirect functionality.

When you call a Web application without adding its runtime \([Tomcat 9](tomcat-9-ddfc101.md) or [TomEE 7](tomee-7-79c039a.md)\) context path to the URL, it will be automatically appended.

**Example**:

If you have configured `/test_context_path` as a context path, and the Web application is available on `/test_app`, when you call:

```
<HOST>:<PORT>/test_app
```

you'll be redirected to:

```
<HOST>:<PORT>/test_context_path/test_app
```

The default context path value for Tomcat and TomEE 7 is ***""*** \(Empty String\).

For more information on how to change this default value, see: [Tomcat 9](tomcat-9-ddfc101.md) and [TomEE 7](tomee-7-79c039a.md).

