<!-- loioa9590c2f5ebc4d1586d9f0f53a60cfdc -->

# TomEE

By default web applications pushed with the SAP Java buildpack are running in an Apache Tomcat container.

Applications could explicitly define the targeted application container - Apache TomEE, by using the TARGET\_RUNTIME environment variable in the application `manifest.yml` file.

> ### Sample Code:  
> manifest.yml
> 
> ```
> ---
> applications:
> - name: <APP_NAME>
>   ...
>   env:
>     TARGET_RUNTIME: tomee
> ```



<a name="loioa9590c2f5ebc4d1586d9f0f53a60cfdc__section_lnr_2bv_42b"/>

## Provided APIs

The *tomee* application runtime container provides the following standard APIs:


<table>
<tr>
<th valign="top">

Runtime



</th>
<th valign="top">

TomEE



</th>
<th valign="top">

Supported Specification Version



</th>
</tr>
<tr>
<td valign="top">

tomee



</td>
<td valign="top">

Apache TomEE JAX-RS \(Java EE 6\)



</td>
<td valign="top">

Java Servlets 3.0

Java ServerPages \(JSP\) 2.2

Expression Language \(EL\) 2.2

Debugging Support for Other Languages 1.0

Standard Tag Library for JavaServer Pages \(JSTL\) 1.2

Java API for WebSocket 1.1

Java ServerFaces \(JSF\) 2.0

Java Transaction API \(JTA\) 1.1

Java Persistence API \(JPA\) 2.0

Java Contexts and Dependency Injection \(CDI\) 1.0

Java Authentication and Authorization Service \(JAAS\)

Java Authorization Contract for Containers \(JACC\) 1.3

JavaMail API 1.4

Bean Validation 1.0

Enterprise JavaBeans 3.1

Java API for RESTful Web Services \(JAX-RS\) 1.1



</td>
</tr>
</table>



<a name="loioa9590c2f5ebc4d1586d9f0f53a60cfdc__section_cq3_nbv_42b"/>

## Customizing the SAP Java Buildpack Defaults

The SAP Java buildpack provides some default configurations for the Apache TomEE application container which could be customized by the application with the [Resource Configuration](resource-configuration-c893e9c.md) feature.

Below is a list with all of the placeholders which could be customized by the application along with their default values:


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

connector.maxHttpHeaderSize



</td>
<td valign="top">

The maximum size of the request and response HTTP header, specified in bytes



</td>
<td valign="top">

8192



</td>
</tr>
<tr>
<td valign="top">

connector.maxThreads



</td>
<td valign="top">

The maximum number of request processing threads to be created by this Connector, which therefore determines the maximum number of simultaneous requests that can be handled



</td>
<td valign="top">

200



</td>
</tr>
<tr>
<td valign="top">

connector.allowTrace



</td>
<td valign="top">

A boolean value which can be used to enable or disable the TRACE HTTP method



</td>
<td valign="top">

false



</td>
</tr>
</table>

To configure the HTTP header size, use:

```
env:
  JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomee/conf/server.xml': {'connector.maxHttpHeaderSize':1024}]"
```

To configure the maximum number of threads, use:

```
env:
  JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomee/conf/server.xml': {'connector.maxThreads':800}]"
```

To enable the TRACE HTTP method, use:

```
env:
  JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomee/conf/server.xml': {'connector.allowTrace':true}]"
```



<a name="loioa9590c2f5ebc4d1586d9f0f53a60cfdc__section_w3t_zc4_2fb"/>

## Configure the maximum number of active sessions

The SAP Java Buildpack provides the default configurations for unlimited sessions for the TomEE application container which could be customized by the application with the [Resource Configuration](resource-configuration-c893e9c.md) feature. To limit the number of active sessions set the *maxActiveSessions* attribute on a *Manager* element, for example:

```
<Context>
  <Manager maxActiveSessions="500" />
</Context>
```



<a name="loioa9590c2f5ebc4d1586d9f0f53a60cfdc__section_i33_1d4_2fb"/>

## Configure the session timeout value

To set session timeout value of active sessions set the *session-config* tag in the application `web.xml`:

```
<session-config>
    <session-timeout>1</session-timeout>
</session-config>
```



<a name="loioa9590c2f5ebc4d1586d9f0f53a60cfdc__section_lbp_bw5_sfb"/>

## Configure the context path attribute

The default value of context path in `server.xml` is ***""*** \(Empty String\). You can override this default value using `app_context_root` in the application `manifest.yml` file. For example:

```
...
  env:
    JBP_CONFIG_TOMCAT: "[tomee:{app_context_root: test_context_path}]"
...
```

