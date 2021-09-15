<!-- loio43934906c1424d07aa13d35b2d5ed564 -->

# responseHeaders

You can add headers that the application router returns to the client in its responses.

You can add response headers to your application, for example, to comply with security standards.

The `responseHeaders` property is an array of objects, each object having the following properties:


<table>
<tr>
<th>

Property



</th>
<th>

Type



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

name



</td>
<td>

string



</td>
<td>

response header name



</td>
</tr>
<tr>
<td>

value



</td>
<td>

string



</td>
<td>

response header value



</td>
</tr>
</table>

```
{ "responseHeaders" : [
    {"name": "header1", "value": "value1"},
    {"name": "header2", "value": "value2"}
  ]
}
```

Example:

> ### Sample Code:  
> ```
> { "responseHeaders" : [
>     {"name": "Content-Security-Policy", "value": "default-src 'self'"}
>   ]
> }
> ```

> ### Note:  
> The response headers are added to the list of additional http headers that you have configured in the *<httpHeaders\>* [environment variable](Environment_Variables_ba52705.md). If the name of a response header configured in the routing configuration is identical with name of an additional http header in the list, the value of the response header overrides the value of the additional http header.

**Related Information**  


[Environment Variables](Environment_Variables_ba52705.md "A list of environment variables that can be used to configure the application router.")

