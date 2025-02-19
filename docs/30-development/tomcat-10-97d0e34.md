<!-- loio97d0e34dcb8f42f4b8f96f7d5c476eb4 -->

# Tomcat 10

By default, web applications pushed with SAP Java Buildpack 2 are running in an Apache Tomcat 10 container.

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



<a name="loio97d0e34dcb8f42f4b8f96f7d5c476eb4__section_lnr_2bv_42b"/>

## Provided APIs

The **tomcat** application runtime container provides the following standard APIs:


<table>
<tr>
<th valign="top">

Runtime

</th>
<th valign="top">

Full Name

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

**Apache Tomcat 10.1.x**

> ### Note:  
> Only relevant for SAP Java Buildpack 2!



</td>
<td valign="top">

Java 11 and later

Java Servlets 6.0

Java Server Pages \(JSP\) 3.1

Expression Language \(EL\) 5.0

Debugging Support for Other Languages 2.0

Java API for WebSocket 2.1

Java Authentication Service Provider Interface for Containers \(JASPIC\) 3.0

. . .

For a full list of specification versions, see: [Apache Tomcat Versions](https://tomcat.apache.org/whichversion.html)

</td>
</tr>
</table>



<a name="loio97d0e34dcb8f42f4b8f96f7d5c476eb4__section_cq3_nbv_42b"/>

## Customize the buildpack defaults

SAP Java Buildpack 2 provides some default configurations for the Apache Tomcat 10 application container. They can be customized by the application with the [Resource Configuration](resource-configuration-c893e9c.md) feature.

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



<a name="loio97d0e34dcb8f42f4b8f96f7d5c476eb4__section_w3t_zc4_2fb"/>

## Configure the maximum number of active sessions

SAP Java Buildpack 2 provides the default configurations for unlimited sessions for the Apache Tomcat 10 application container. They can be customized by the application with the [Resource Configuration](resource-configuration-c893e9c.md) feature. To limit the number of active sessions, set the *maxActiveSessions* attribute on a *Manager* element. For example:

> ### Example:  
> ```
> <Context>
>   <Manager maxActiveSessions="500" />
> </Context>
> ```



<a name="loio97d0e34dcb8f42f4b8f96f7d5c476eb4__section_i33_1d4_2fb"/>

## Configure the session timeout value

To set session timeout value of active sessions, set the *<session-config\>* tag in the application's `web.xml` file:

> ### Example:  
> ```
> <session-config>
>     <session-timeout>1</session-timeout>
> </session-config>
> ```



<a name="loio97d0e34dcb8f42f4b8f96f7d5c476eb4__section_lbp_bw5_sfb"/>

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

