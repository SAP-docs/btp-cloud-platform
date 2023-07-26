<!-- loio79c039ab43b946a7b50c5d0326a3b40b -->

# TomEE 7

By default, web applications deployed with SAP Java Buildpack are running in an Apache Tomcat container.

Applications can explicitly define the target application container by using the TARGET\_RUNTIME environment variable in the application's `manifest.yml` file

> ### Example:  
> ```
> 
> ---
> applications:
> - name: myapp
>   ...
>   env:
>     TARGET_RUNTIME: tomee7
> ```



<a name="loio79c039ab43b946a7b50c5d0326a3b40b__section_lnr_2bv_42b"/>

## Provided APIs

The **tomee7** application runtime container provides the following standard APIs:


<table>
<tr>
<th valign="top">

Runtime



</th>
<th valign="top">

TomEE 7



</th>
<th valign="top">

Supported Specification Version



</th>
</tr>
<tr>
<td valign="top">

tomee7



</td>
<td valign="top">

Apache TomEE 7 \(*Java EE 7 Web Profile*\)



</td>
<td valign="top">

Java Servlet 3.1

JavaServer Pages \(JSP\) 2.3

Expression Language \(EL\) 3.0

WebSocket 1.1

Standard Tag Library for JavaServer Pages \(JSTL\) 1.2

Java API for RESTful Web Services \(JAX-RS\) 2.0

JavaServer Faces \(JSF\) 2.2

Debugging Support for Other Languages 1.0

Enterprise JavaBeans \(EJB\) Lite 3.2

Java Transaction API \(JTA\) 1.2

Java Persistence API \(JPA\) 2.1

Bean Validation 1.1

Managed Beans 1.0

Interceptors 1.2

Common Annotations for Java Platform 1.2

Dependency Injection for Java 1.0

Contexts and Dependency Injection for Java EE platform 1.1



</td>
</tr>
</table>



<a name="loio79c039ab43b946a7b50c5d0326a3b40b__section_cq3_nbv_42b"/>

## Customizing the SAP Java Buildpack Defaults

SAP Java Buildpack provides some default configurations for the Apache TomEE 7 application container. They can be customized by the application with the [Resource Configuration](resource-configuration-c893e9c.md) feature.

Below is a list of all the placeholders that can be customized by the application, along with their default values:


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
  JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomee7/conf/server.xml': {'connector.maxHttpHeaderSize':1024}]"
```

To configure the maximum number of threads, use:

```
env:
  JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomee7/conf/server.xml': {'connector.maxThreads':800}]"
```

To enable the TRACE HTTP method, use:

```
env:
  JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomee7/conf/server.xml': {'connector.allowTrace':true}]"
```



<a name="loio79c039ab43b946a7b50c5d0326a3b40b__section_w3t_zc4_2fb"/>

## Configure the maximum number of active sessions

SAP Java Buildpack provides the default configurations for unlimited sessions for the Apache TomEE 7 application container. They can be customized by the application with the [Resource Configuration](resource-configuration-c893e9c.md) feature. To limit the number of active sessions, set the *maxActiveSessions* attribute on a *Manager* element. For example:

> ### Example:  
> ```
> <Context>
>   <Manager maxActiveSessions="500" />
> </Context>
> ```



<a name="loio79c039ab43b946a7b50c5d0326a3b40b__section_i33_1d4_2fb"/>

## Configure the session timeout value

To set session timeout value of active sessions, set the *<session-config\>* tag in the application's `web.xml` file:

> ### Example:  
> ```
> <session-config>
>     <session-timeout>1</session-timeout>
> </session-config>
> ```



<a name="loio79c039ab43b946a7b50c5d0326a3b40b__section_lbp_bw5_sfb"/>

## Configure the context path attribute

The default value of context path in `server.xml` is ***""*** \(Empty String\). You can override this default value by using `app_context_root` in the application's `manifest.yml` file. For example:

> ### Example:  
> ```
> 
> ...
>   env:
>     JBP_CONFIG_TOMCAT: "[tomee7:{app_context_root: test_context_path}]"
> ...
> ```

