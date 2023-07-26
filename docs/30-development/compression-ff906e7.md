<!-- loioff906e7f99dd4b3a814fbf696433ed99 -->

# compression

The `compression` keyword enables you to define if the application router compresses text resources before sending them.



By default, resources larger than 1KB are compressed. If you need to change the compression size threshold, for example, to “2048 bytes”, you can add the optional property <code>“minSize”</code>: *<size\_in\_KB\>*, as illustrated in the following example.

> ### Sample Code:  
> ```
> {
>   "compression": {
>       "minSize": 2048
>   }
> }
> ```

You can disable compression in the following ways:

-   Global

    Within the compression section add "enabled": false

-   Front end

    The client sends a header “`Accept-Encoding`” which does not include “`gzip`”.

-   Back end

    The application sends a header “`Cache-Control`” with the “`no-transform`” directive.


**Application Router: Compression Properties**


<table>
<tr>
<th valign="top">

Property



</th>
<th valign="top">

Type



</th>
<th valign="top">

Mandatory



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

`minSize` 



</td>
<td valign="top">

Number



</td>
<td valign="top">

No



</td>
<td valign="top">

Text resources larger than this size will be compressed.



</td>
</tr>
<tr>
<td valign="top">

`enabled` 



</td>
<td valign="top">

Boolean



</td>
<td valign="top">

No



</td>
<td valign="top">

Globally disables or enables compression. The default value is true.



</td>
</tr>
<tr>
<td valign="top">

`compressResponseMixedTypeContent` 



</td>
<td valign="top">

Boolean



</td>
<td valign="top">

No



</td>
<td valign="top">

Determines whether response content of the multipart / mixed content type should be compressed. The default value is `false`.



</td>
</tr>
</table>

> ### Note:  
> If the *<COMPRESSION\>* environment variable is set it will overwrite any existing values.

