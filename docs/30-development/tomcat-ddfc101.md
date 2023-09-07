<!-- loioddfc10180fe844049cc71f6989942dc2 -->

# Tomcat

By default, web applications pushed with SAP Java Buildpack are running in an Apache Tomcat container.

Applications can explicitly define the target application container by using the TARGET\_RUNTIME environment variable in the application's `manifest.yml` file.

> ### Example:  
> ```
> 
> ---
> applications:
> - name: myapp
>   ...
>   env:
>     TARGET_RUNTIME: tomcat
> ```



<a name="loioddfc10180fe844049cc71f6989942dc2__section_lnr_2bv_42b"/>

## Provided APIs

The **tomcat** application runtime container provides the following standard APIs:


<table>
<tr>
<th valign="top">

Runtime



</th>
<th valign="top">

Tomcat



</th>
<th valign="top">

Supported Specification Version



</th>
</tr>
<tr>
<td valign="top">

tomcat



</td>
<td valign="top">

Apache Tomcat 9



</td>
<td valign="top">

Java Servlets 4.0

Java Server Pages \(JSP\) 2.3

Expression Language \(EL\) 3.0

Debugging Support for Other Languages 1.0

Java API for WebSocket 1.1

Java Authentication Service Provider Interface for Containers \(JASPIC\) 1.1

For more information, see [Apache Tomcat: Tomcat Versions](https://tomcat.apache.org/whichversion.html)



</td>
</tr>
</table>



<a name="loioddfc10180fe844049cc71f6989942dc2__section_cq3_nbv_42b"/>

## Customizing the SAP Java Buildpack Defaults

SAP Java Buildpack provides some default configurations for the Apache Tomcat application container. They can be customized by the application with the [Resource Configuration](resource-configuration-c893e9c.md) feature.

Below is a list of all the placeholders than can be customized by the application, along with their default values:


<table>
<tr>
<th valign="top">

Placeholder



</th>
<th valign="top">

Description



</th>
<th valign="top">

Default Value



</th>
</tr>
<tr>
<td valign="top">

`connector.maxHttpHeaderSize` 



</td>
<td valign="top">

The maximum size of the request and response HTTP header, specified in bytes



</td>
<td valign="top">

**8192** 



</td>
</tr>
<tr>
<td valign="top">

`connector.maxThreads` 



</td>
<td valign="top">

The maximum number of request processing threads to be created by this Connector, which therefore determines the maximum number of simultaneous requests that can be handled



</td>
<td valign="top">

**200** 



</td>
</tr>
<tr>
<td valign="top">

`connector.allowTrace` 



</td>
<td valign="top">

A Boolean value that enables or disables the TRACE HTTP method



</td>
<td valign="top">

**false** 



</td>
</tr>
</table>

To configure the HTTP header size, use:

```
env:
  JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomcat/conf/server.xml': {'connector.maxHttpHeaderSize':1024}]"
```

To configure the maximum number of threads, use:

```
env:
  JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomcat/conf/server.xml': {'connector.maxThreads':800}]"
```

To enable the TRACE HTTP method, use:

```
env:
  JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomcat/conf/server.xml': {'connector.allowTrace':true}]"
```



<a name="loioddfc10180fe844049cc71f6989942dc2__section_w3t_zc4_2fb"/>

## Configure the maximum number of active sessions

SAP Java Buildpack provides the default configurations for unlimited sessions for the Apache Tomcat application container. They can be customized by the application with the [Resource Configuration](resource-configuration-c893e9c.md) feature. To limit the number of active sessions, set the *maxActiveSessions* attribute on a *Manager* element. For example:

> ### Example:  
> ```
> <Context>
>   <Manager maxActiveSessions="500" />
> </Context>
> ```



<a name="loioddfc10180fe844049cc71f6989942dc2__section_i33_1d4_2fb"/>

## Configure the session timeout value

To set session timeout value of active sessions, set the *<session-config\>* tag in the application's `web.xml` file:

> ### Example:  
> ```
> <session-config>
>     <session-timeout>1</session-timeout>
> </session-config>
> ```



<a name="loioddfc10180fe844049cc71f6989942dc2__section_lbp_bw5_sfb"/>

## Configure the context path attribute

The default value of context path in `server.xml` is ***""*** \(Empty String\). You can override this default value by using *app\_context\_root* in the application's `manifest.yml` file. For example:

> ### Example:  
> ```
> 
> ...
>   env:
>     JBP_CONFIG_TOMCAT: "[tomcat:{app_context_root: test_context_path}]"
> ...
> ```



<a name="loioddfc10180fe844049cc71f6989942dc2__section_gz5_3ns_zxb"/>

## Configure the cookie processor

In Tomcat 8.5.84, a custom cookie processor has been created, based on the RFC 6265 Cookie Processor. If the PROCESS\_COOKIE environment variable is set to **true**, then this new cookie processor will override the default one.

**Reason**: In Tomcat Apache 8.5.84, the date format used with the *expires* attribute of HTTP cookies was corrected to be compliant with RFC 6265. A single space rather than a single dash is now used to separate the day, month, and year components. For more information, see [Apache Tomcat: Tomcat 8 Changelog](https://tomcat.apache.org/tomcat-8.5-doc/changelog.html)

The purpose of the new cookie processor is to set the *Cookie Expire* date to format with '-' \(*dash*\) delimiter instead of ' ' \(*space*\) so that no errors would be thrown.

Below is a sample error message thrown when **not** using the new customization:

> ### Example:  
> ```
> Sample error: "Invalid cookie header: "set-cookie: username=John; Max-Age=21; Expires=Thu, 17 Aug 2023 13:31:55 GMT". Invalid 'expires' attribute: Thu, 17 Aug 2023 13:31:55 GMT "
> ```

