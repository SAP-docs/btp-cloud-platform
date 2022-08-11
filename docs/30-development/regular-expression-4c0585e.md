<!-- loio4c0585e31d564ca7a7d46f4f910a201b -->

# Regular Expression

Regular expressions can be used to match strings against patterns or extract substrings that match certain criteria.



The regular expression engines offered by XCO are based on the standards offered by CL\_ABAP\_REGEX:

-   POSIX

-   PCRE

-   XPATH2

-   XSD


In XCO, these regular expression standards are encapsulated in the IF\_XCO\_REGEX\_ENGINE abstraction which is accessible via the XCO\_CP\_REGULAR\_EXPRESSION API:

> ### Sample Code:  
> ```abap
> 
> " Example for a POSIX regular expression engine (More configuration options are available
> " as optional parameters of the method POSIX).
> DATA(lo_posix_engine) = xco_cp_regular_expression=>engine->posix(
>   iv_ignore_case = abap_true
> ).
> 
> " Example for a PCRE regular expression engine (More configuration options are available
> " as optional parameters of the method PCRE).
> DATA(lo_pcre_engine) = xco_cp_regular_expression=>engine->pcre(
>   iv_ignore_case      = abap_false
>   iv_enable_multiline = abap_false
> ).
> 
> " Example for an XPATH 2.0 regular expression engine (More configuration options are available
> " as optional parameters of the method XPATH2).
> DATA(lo_xpath2_engine) = xco_cp_regular_expression=>engine->xpath2(
>   iv_ignore_case      = abap_true
>   iv_enable_multiline = abap_false
> ).
> 
> " Example for an XSD regular expression engine (More configuration options are available
> " as optional parameters of the method XSD).
> DATA(lo_xsd_engine) = xco_cp_regular_expression=>engine->xsd(
>   iv_ignore_case      = abap_true
>   iv_enable_multiline = abap_false
> ).
> ```

The parameters of the regular expression engine factory methods can be used to configure the behavior of the engine when it is used against a string. The default engine \(which is used when no explicit engine is supplied\) is POSIX in the default configuration as provided by CL\_ABAP\_REGEX.

A regular expression can be used to easily check if a given string matches a pattern

> ### Sample Code:  
> ```abap
> " LV_CASE_INSENSITIVE_MATCHES will have the value abap_true as
> " LO_POSIX_ENGINE is case insensitive (see above).
> DATA(lv_case_insensitive_matches) = xco_cp=>string( |abc| )->matches(
>   iv_regular_expression = '^a.*C$'
>   io_engine             = lo_posix_engine
> ).
> 
> " LV_CASE_SENSITIVE_MATCHES will have the value abap_false as the
> " default POSIX engine is case sensitive.
> DATA(lv_case_sensitive_matches) = xco_cp=>string( |abc| )->matches( '^a.*C$' ).
> ```

or to retrieve certain parts from it

> ### Sample Code:  
> ```abap
> DATA(lo_name_parts) = xco_cp=>string( |John Doe| )->grep( '^(\S+)\s+(\S+)$' ).
> 
> " LV_FIRST_NAME = John
> DATA(lv_first_name) = lo_name_parts->value[ 1 ].
> 
> " LV_LAST_NAME = Doe
> DATA(lv_last_name) = lo_name_parts->value[ 2 ].
> ```

