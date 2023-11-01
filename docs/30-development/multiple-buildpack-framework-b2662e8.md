<!-- loiob2662e8e6e50459a9af38c6daba66f06 -->

# Multiple Buildpack Framework

The Multiple Buildpack Framework enables the SAP Java Buildpack to act as the final buildpack in a multiple buildpack deployment. It reads the contributions of other, earlier buildpacks and incorporates them into its standard staging.

> ### Note:  
> If you try to use the SAP Java Buildpack as a non-final buildpack, an error will be thrown.

When the Java Buildpack acts as the final buildpack in a multiple buildpack deployment it honors the following core contract integration points with non-final buildpacks.


<table>
<tr>
<th valign="top">

Integration Point

</th>
<th valign="top">

Buildpack Usage

</th>
</tr>
<tr>
<td valign="top">

`/bin`

</td>
<td valign="top">

An existing `/bin` directory contributed by a non-final buildpack will be added to the *<$PATH\>* of the application as it executes.

</td>
</tr>
<tr>
<td valign="top">

`/lib`

</td>
<td valign="top">

An existing `/lib` directory contributed by a non-final buildpack will be added to the *<$LD\_LIBRARY\_PATH\>* of the application as it executes.

</td>
</tr>
</table>

