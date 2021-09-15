<!-- loioff906e7f99dd4b3a814fbf696433ed99 -->

# compression

The `compression` keyword enables you to define if the application router compresses text resources before sending them.



By default, resources larger than 1KB are compressed. If you need to change the compression size threshold, for example, to “2048 bytes”, you can add the optional property `“minSize”`: *<size\_in\_KB\>*, as illustrated in the following example.

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


<a name="loioff906e7f99dd4b3a814fbf696433ed99__table_ikc_z2n_tx"/>Application Router: Compression Properties


<table>
<tr>
<th>

Property



</th>
<th>

Type



</th>
<th>

Mandatory



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

 `minSize` 



</td>
<td>

Number



</td>
<td>

No



</td>
<td>

Text resources larger than this size will be compressed.



</td>
</tr>
<tr>
<td>

 `enabled` 



</td>
<td>

Boolean



</td>
<td>

No



</td>
<td>

Globally disables or enables compression. The default value is true.



</td>
</tr>
</table>

> ### Note:  
> If the *<COMPRESSION\>* environment variable is set it will overwrite any existing values.

