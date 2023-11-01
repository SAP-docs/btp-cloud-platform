<!-- loio063ad163cf7d4dcaa1073eecc12e2225 -->

# String

Besides providing a straightforward integration with regular expressions \(see [Regular Expression](regular-expression-4c0585e.md)\), the XCO string abstraction offers further simplifications when working with strings.





### The methods TO and FROM

The methods TO and FROM provide flexible ways to extract a substring from a string. Their functionality is based on the following character indexing scheme \(The table is based on the example string ABCDEF\):


<table>
<tr>
<th valign="top">

A

</th>
<th valign="top">

B

</th>
<th valign="top">

C

</th>
<th valign="top">

D

</th>
<th valign="top">

E

</th>
<th valign="top">

F

</th>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

2

</td>
<td valign="top">

3

</td>
<td valign="top">

4

</td>
<td valign="top">

5

</td>
<td valign="top">

6

</td>
</tr>
<tr>
<td valign="top">

\-6

</td>
<td valign="top">

\-5

</td>
<td valign="top">

\-4

</td>
<td valign="top">

\-3

</td>
<td valign="top">

\-2

</td>
<td valign="top">

\-1

</td>
</tr>
</table>

Both TO and FROM have an inclusive behavior, i.e. the provided index is always included in the retrieved substring. Furthermore, if the provided index is out of bounds the behavior is as if the index had pointed to the first \(resp. last\) character of the string.

The following sample illustrates several usages:

> ### Sample Code:  
> ```abap
> DATA(lo_string) = xco_cp=>string( |ABCDEF| ).
> 
> " LV_SUBSTRING_1 = DEF
> DATA(lv_substring_1) = lo_string->from( 4 )->value.
> 
> " LV_SUBSTRING_2 = DEF
> DATA(lv_substring_2) = lo_string->from( -3 )->value.
> 
> " LV_SUBSTRING_3 = ABC
> DATA(lv_substring_3) = lo_string->to( 3 )->value.
> 
> " LV_SUBSTRING_4 = ABC
> DATA(lv_substring_4) = lo_string->to( -4 )->value.
> 
> " LV_SUBSTRING_5 = CD
> DATA(lv_substring_5) = lo_string->from( 3 )->to( 2 )->value.
> 
> " LV_SUBSTRING_6 = BC
> DATA(lv_substring_6) = lo_string->to( -4 )->from( 2 )->value.
> ```



### Splitting and joining

The XCO string library also provides a way to split strings and join a list of strings:

> ### Sample Code:  
> ```abap
> DATA(lo_name_parts) = xco_cp=>string( |John Doe| )->split( | | ).
> 
> " LV_REVERSED_NAME = Doe, John
> DATA(lv_reversed_name) = lo_name_parts->reverse( )->join( |, | )->value.
> ```



### Composing and decomposing

A generalization of split and join operations on strings are string compositions and decompositions.

String compositions and decompositions encapsulate algorithms which can transform a string to a list of strings \(decomposition\) and vice versa \(composition\) according to a certain formula. Currently, both Camel Case and Pascal Case are supported in both directions.

The following example illustrates how the camel case composition and decomposition can be used to easily translate between underscore and camel case notation.

> ### Sample Code:  
> ```abap
> DATA(lv_string_with_underscores) = |FIRST_NAME|.
> 
> " LV_STRING_IN_CAMEL_CASE = firstName
> DATA(lv_string_in_camel_case) = xco_cp=>string( lv_string_with_underscores
>   )->split( |_|
>   )->compose( xco_cp_string=>composition->camel_case
>   )->value.
> 
> " LV_RESTORED_STRING = FIRST_NAME
> DATA(lv_restored_string) = xco_cp=>string( lv_string_in_camel_case
>   )->decompose( xco_cp_string=>decomposition->camel_case
>   )->join( |_|
>   )->to_upper_case(
>   )->value.
> ```



### Converting strings to xstrings

Converting a given string to its xstring representation for a given code page can be easily accomplished by making use of `IF_XCO_CHAR_CODE_PAGE`s which are available via `XCO_CP_CHARACTER`:

> ### Sample Code:  
> ```abap
> DATA(lv_string) = |ABC|.
> 
> " The representation of LV_STRING as an XSTRING where the given character
> " code page is used for the conversion.
> DATA(lv_xstring) = xco_cp=>string( lv_string
>   )->as_xstring( xco_cp_character=>code_page->utf_8 ).
> ```



<a name="loio063ad163cf7d4dcaa1073eecc12e2225__section_vzv_vh4_3tb"/>

## Calculating Hash Codes

Calculating the hash value of a given string for a given hash algorithm can be accomplished as follows:

> ### Sample Code:  
> ```abap
> " Upon execution, LV_HASH_VALUE will have the value C79C561BB2CC3D0430A54B3D014C89C3089FE089.
> DATA(lv_hash_value) = xco_cp=>string( 'MY_STRING'
>   )->as_xstring( xco_cp_hash=>algorithm->sha_1
>   )->value.
> ```

Note the following details:

-   Supported hash algorithms \(represented as objects of type IF\_XCO\_HASH\_ALGORITHM\) can be obtained via XCO\_CP\_HASH=\>ALGORITHM. The SHA-1 hash algorithm is statically available via the SHA\_1 property while the FOR method can be used to obtain hash algorithms based on their string identifiers, e.g. XCO\_CP\_HASH=\>ALGORITHM→FOR\( 'MD5' \) for the MD5 hash algorithm

-   When calculating the hash value of a string, an IF\_XCO\_HASH\_ALGORITHM object acts as an IF\_XCO\_STRING\_XSTRING\_CNVRSN, where the XSTRING that is derived from the string corresponds to the hash value


