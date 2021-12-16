<!-- loio83d241613dcd41c99ccc308ed0d26399 -->

# Application Containers

The following application containers are available for usage with the SAP Java Buildpack.



-   [Tomcat](application-containers-83d2416.md#loioddfc10180fe844049cc71f6989942dc2)

-   [TomEE](application-containers-83d2416.md#loioa9590c2f5ebc4d1586d9f0f53a60cfdc)

-   [TomEE 7](application-containers-83d2416.md#loio79c039ab43b946a7b50c5d0326a3b40b)

-   [Java Main](application-containers-83d2416.md#loio8a1786acd70445768b35e50f3038a2a9)


 <a name="loioddfc10180fe844049cc71f6989942dc2"/>

<!-- loioddfc10180fe844049cc71f6989942dc2 -->

## Tomcat

By default web applications pushed with the SAP Java buildpack are running in an Apache Tomcat container.

Applications could explicitly define the targeted application container by using the TARGET\_RUNTIME environment variable in the application `manifest.yml` file.

> ### Sample Code:  
> manifest.yml
> 
> ```
> ---
> applications:
> - name: <APP_NAME>
>   ...
>   env:
>     TARGET_RUNTIME: tomcat
> ```



<a name="loioddfc10180fe844049cc71f6989942dc2__section_lnr_2bv_42b"/>

## Provided APIs

The tomcat application runtime container provides the following standard APIs:


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

Apache Tomcat 8



</td>
<td valign="top">

Java Servlets 3.1

Java ServerPages \(JSP\) 2.3

Expression Language \(EL\) 3.0

Debugging Support for Other Languages 1.0

Java API for WebSocket 1.1



</td>
</tr>
</table>



<a name="loioddfc10180fe844049cc71f6989942dc2__section_cq3_nbv_42b"/>

## Customizing the SAP Java Buildpack Defaults

SAP Java Buildpack provides some default configurations for the Tomcat application container which could be customized by the application with the [Resource Configuration](resource-configuration-c893e9c.md) feature.

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

The SAP Java Buildpack provides the default configurations for unlimited sessions for the Tomcat application container which could be customized by the application with the [Resource Configuration](resource-configuration-c893e9c.md) feature. To limit the number of active sessions set the *maxActiveSessions* attribute on a *Manager* element, for example:

```
<Context>
  <Manager maxActiveSessions="500" />
</Context>
```



<a name="loioddfc10180fe844049cc71f6989942dc2__section_i33_1d4_2fb"/>

## Configure the session timeout value

To set session timeout value of active sessions set the *session-config* tag in the application `web.xml`:

```
<session-config>
    <session-timeout>1</session-timeout>
</session-config>
```



<a name="loioddfc10180fe844049cc71f6989942dc2__section_lbp_bw5_sfb"/>

## Configure the context path attribute

The default value of context path in `server.xml` is ***""*** \(Empty String\). You can override this default value using `app_context_root` in the application `manifest.yml` file. For example:

```
...
  env:
    JBP_CONFIG_TOMCAT: "[tomcat:{app_context_root: test_context_path}]"
...
```

 <a name="loioa9590c2f5ebc4d1586d9f0f53a60cfdc"/>

<!-- loioa9590c2f5ebc4d1586d9f0f53a60cfdc -->

## TomEE

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

 <a name="loio79c039ab43b946a7b50c5d0326a3b40b"/>

<!-- loio79c039ab43b946a7b50c5d0326a3b40b -->

## TomEE 7

By default web applications pushed with the SAP Java buildpack are running in an Apache Tomcat container.

Applications could explicitly define the targeted application container - Apache TomEE 7, by using the TARGET\_RUNTIME environment variable in the application `manifest.yml` file.

> ### Sample Code:  
> manifest.yml
> 
> ```
> ---
> applications:
> - name: <APP_NAME>
>   ...
>   env:
>     TARGET_RUNTIME: tomee7
> ```



<a name="loio79c039ab43b946a7b50c5d0326a3b40b__section_lnr_2bv_42b"/>

## Provided APIs

The tomee7 application runtime container provides the following standard APIs:


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

Apache TomEE 7 \(Java EE 7 Web Profile\)



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

The SAP Java Buildpack provides some default configurations for the Apache TomEE 7 application container which could be customized by the application with the [Resource Configuration](resource-configuration-c893e9c.md) feature.

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

The SAP Java Buildpack provides the default configurations for unlimited sessions for the TomEE 7 application container which could be customized by the application with the [Resource Configuration](resource-configuration-c893e9c.md) feature. To limit the number of active sessions set the *maxActiveSessions* attribute on a *Manager* element, for example:

```
<Context>
  <Manager maxActiveSessions="500" />
</Context>
```



<a name="loio79c039ab43b946a7b50c5d0326a3b40b__section_i33_1d4_2fb"/>

## Configure the session timeout value

To set session timeout value of active sessions set the *session-config* tag in the application `web.xml`:

```
<session-config>
    <session-timeout>1</session-timeout>
</session-config>
```



<a name="loio79c039ab43b946a7b50c5d0326a3b40b__section_lbp_bw5_sfb"/>

## Configure the context path attribute

The default value of context path in `server.xml` is ***""*** \(Empty String\). You can override this default value using `app_context_root` in the application `manifest.yml` file. For example:

```
...
  env:
    JBP_CONFIG_TOMCAT: "[tomee7:{app_context_root: test_context_path}]"
...
```

 <a name="loio8a1786acd70445768b35e50f3038a2a9"/>

<!-- loio8a1786acd70445768b35e50f3038a2a9 -->

## Java Main

You can create a Java application that starts its own run time. This allows the usage of frameworks and java runtimes, such as Spring Boot, Jetty, Undertow, or Netty.



<a name="loio8a1786acd70445768b35e50f3038a2a9__prereq_vsk_wdv_42b"/>

## Prerequisites

-   You are not using the [Resource Configuration](resource-configuration-c893e9c.md) feature of the buildpack.

> ### Note:  
> The resource configurations needed for the database connection are not applicable for the Java Main applications. For more information about database connections, see Related Information.



## Context

In this section such applications will be referred to as Java Main applications. The application container provided by the SAP Java Buildpack for running Java Main applications is referred as Java Main container.



## Procedure

1.  Make sure your built JAR archive is configured properly.

    Regardless of the tool you use to build your Java application, you have to make sure that the following tasks are performed:

    1.  You have built a JAR archive.

    2.  You have specified a main class in the `META-INF/MANIFEST.MF` file of the JAR archive.

        > ### Sample Code:  
        > Manifest.MF
        > 
        > ```
        > Manifest-Version: 1.0
        > Archiver-Version: Plexus Archiver
        > Built-By: p123456
        > Created-By: Apache Maven 3.3.3
        > Build-Jdk: 1.8.0_45
        > Main-Class: com.companya.xs.java.main.Controller  
        > ```

    3.  You have packaged all your dependent libraries in the JAR file, also known as creating an uber JAR or a fat JAR.


    If you are using Maven as your build tool, you can use the `maven-shade-plugin` to perform the above tasks.

    > ### Sample Code:  
    > Sample configuration for the `maven-shade-plugin`
    > 
    > ```
    > <build>
    > <finalName>java-main-sample</finalName>
    > <plugins>
    >   <plugin>
    >     <groupId>org.apache.maven.plugins</groupId>
    >     <artifactId>maven-shade-plugin</artifactId>
    >     <version>2.4.3</version>
    >     <configuration>
    >       <createDependencyReducedPom>false</createDependencyReducedPom>
    >       <filters>
    >         <filter>
    >           <artifact>*:*</artifact>
    >           <excludes>
    >             <exclude>META-INF/*.SF</exclude>
    >             <exclude>META-INF/*.DSA</exclude>
    >             <exclude>META-INF/*.RSA</exclude>
    >           </excludes>
    >         </filter>
    >       </filters>
    >     </configuration>
    >     <executions>
    >       <execution>
    >         <phase>package</phase>
    >         <goals>
    >           <goal>shade</goal>
    >         </goals>
    >         <configuration>
    >           <transformers>
    >             <transformer implementation="org.apache.maven.plugins.shade.resource.ServicesResourceTransformer" />
    >             <transformer implementation="org.apache.maven.plugins.shade.resource.ManifestResourceTransformer">
    >               <manifestEntries>
    >                 <Main-Class>com.sap.xs.java.main.Controller</Main-Class>
    >               </manifestEntries>
    >             </transformer>
    >           </transformers>
    >         </configuration>
    >       </execution>
    >     </executions>
    >   </plugin>
    > </plugins>
    > </build>
    > ```

2.  Configure the `manifest.yml`.

    To be able to push the Java Main application, you need to specify the path to the `.jar` archive in the `manifest.yml` file.

    > ### Sample Code:  
    > manifest.yml
    > 
    > ```
    > ---
    > applications:
    > - name: java-main
    >   memory: 128M
    >   path: ./target/java-main-sample.jar
    >   instances: 1
    > ```

3.  Push the application to Cloud Foundry.

    For the purpose use `cf push` command.




Donna Moore would like to create a Java Main application to use its own run time. For that purpose she performs the following steps:

1.  Creates a *sample\_main* application. Using Spring Boot for that purpose.

2.  Navigates to the `sample_main` directory of the application, using the command line tool, and builds it. She can perform this operation with the command `mvn clean install`.

3.  After the build is successful, she checks that the `sample_main` directory of the application, contains a sample\_main.jar file.

4.  She opens the sample\_main.jar file and checks that the `META-INF/MANIFEST.MF` file contains the Main-Class header with value, the name of the main class.

5.  She adds the path to the JAR file in the `manifest.yml` file.

    She needs to do that to make sure that the application can be pushed to the Cloud Foundry Environment. For that purpose, she adds the following line in the `manifest.yml` file:

    ```
    path: ./target/sample_main.jar
    ```

6.  Finally, she pushes the Java Main application with the following command:

    ```
    cf push sample_main
    ```


**Related Information**  


[Configuring a Database Connection](configuring-a-database-connection-7568c3d.md#loio7568c3d036f34a64bb6595b55805bffb "Define details of the database connection used by your Java Web Application running on Cloud Foundry Environment with the SAP Java Buildpack.")

