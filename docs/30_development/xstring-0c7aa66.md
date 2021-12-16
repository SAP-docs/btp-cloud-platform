<!-- loio0c7aa6642b294709abcc0e3de0488f1a -->

# XString

To offer a convenient way to incorporate standard operations on binary data into application logic, the XCO Library provides a standard abstraction for xstrings, `IF_XCO_XSTRING`, that is tightly integrated with the XCO string abstraction `IF_XCO_STRING`.



## Using the Base64 binary-to-text encoding

Built-in conversions are provided to support working with the Base64 binary-to-text encoding. Encoding raw binary data to its Base64 representation and decoding a given Base64 representation to its underlying binary data can be accomplished as follows:

> ### Sample Code:  
> ```lang-abap
> " LV_XSTRING can store arbitrary binary data.
> DATA lv_xstring TYPE xstring.
> 
> " LV_BASE64_ENCODING is of type STRING and contains the Base64 encoded version
> " of LV_XSTRING.
> DATA(lv_base64_encoding) = xco_cp=>xstring( lv_xstring
>   )->as_string( xco_cp_binary=>text_encoding->base64
>   )->value.
> 
> " LV_ORIGINAL_XSTRING is of type XSTRING and contains the binary data encoded
> " in LV_BASE64_ENCODING
> DATA(lv_original_xstring) = xco_cp=>string( lv_base64_encoding
>   )->as_xstring( xco_cp_binary=>text_encoding->base64
>   )->value.
> ```



<a name="loio0c7aa6642b294709abcc0e3de0488f1a__section_fhr_f53_wrb"/>

## Using code pages

An xstring can also be converted to a string by using a code page, e.g. UTF-8:

> ### Sample Code:  
> ```lang-abap
> DATA(lv_string) = xco_cp=>xstring( lv_xstring
>   )->as_string( xco_cp_character=>code_page->utf_8
>   )->value.
> ```

