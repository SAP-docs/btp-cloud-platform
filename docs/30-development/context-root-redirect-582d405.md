<!-- loio582d4056ea7c44a7a315e37ca2a5a64b -->

# Context Root Redirect

SAP Java Buildpack provides a context root redirect functionality.

When you call a Web application without adding its [runtime](runtimes-and-containers-83d2416.md) context path to the URL, it's automatically appended.



<a name="loio582d4056ea7c44a7a315e37ca2a5a64b__section_whg_hwv_jcc"/>

## Example

If you configure `/my_context_path` as a context path, and the Web application is available on `/my_app`, then:


<table>
<tr>
<th valign="top">

When you call:

</th>
<th valign="top">

You'll be redirected to:

</th>
</tr>
<tr>
<td valign="top">

```
<HOST>:<PORT>/my_app
```



</td>
<td valign="top">

```
<HOST>:<PORT>/my_context_path/my_app
```



</td>
</tr>
</table>

The default context path value for Tomcat and TomEE is *****""***** \(empty string\).

For more information on how to change the default value, see:

-   [Tomcat 9](tomcat-9-ddfc101.md)

-   [Tomcat 10](tomcat-10-97d0e34.md)

-   [TomEE 7](tomee-7-79c039a.md)

-   [TomEE 10](tomee-10-66e808e.md)


