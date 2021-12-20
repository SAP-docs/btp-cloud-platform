<!-- loio492ccdb87b224a35a8ed20e53325dfce -->

# JSON



The goal of the XCO JSON module is to make working with JSON data as simple as possible. This includes the creation of JSON strings \(both from ABAP data structures and from scratch\) as well as the translation of JSON strings to ABAP.



### Reading JSON strings

The following code shows an example of how a JSON string \(e.g. the response of an outbound service call\) can be translated into a corresponding ABAP structure:

> ### Sample Code:  
> ```lang-abap
> DATA(lv_json_string) = '{'
>   && |"SessionId":"7cd44fff-036a-4155-b0d2-f5a4dfbcee92",|
>   && |"UserName":"John Doe",|
>   && |"IsPremiumUser":true|
>   && '}'.
> 
> TYPES:
>   BEGIN OF ts_input,
>     session_id      TYPE sysuuid_c36,
>     user_name       TYPE string,
>     is_premium_user TYPE abap_bool,
>   END OF ts_input.
> 
> DATA ls_input TYPE ts_input.
> 
> " After execution, the structure components will have the following values
> "  session_id = 7cd44fff-036a-4155-b0d2-f5a4dfbcee92
> "  user_name = John Doe
> "  is_premium_user = X
> xco_cp_json=>data->from_string( lv_json_string )->apply( VALUE #(
>   ( xco_cp_json=>transformation->pascal_case_to_underscore )
>   ( xco_cp_json=>transformation->boolean_to_abap_bool )
> ) )->write_to( REF #( ls_input ) ).
> ```

To make it easy to adjust JSON data to ABAP requirements \(e.g. to switch between camel case and underscore notation\) the XCO library provides built-in transformations which are accessible via the XCO\_CP\_JSON API. The current version of the XCO library comes with the following three built-in transformations:

-   Camel case/Pascal case to underscore: Transforms the name of each object member in the JSON data from Camel case/Pascal case to underscore notation
-   Underscore to Camel case/Pascal case: Transforms the name of each object member in the JSON data from underscore to Camel case/Pascal case notation
-   Boolean to abap\_bool: Transforms each JSON boolean value to its abap\_bool equivalent, i.e. true becomes ‘X’ and false becomes ‘’

Note that the XCO library uses the following terminology:

• Camel case: The first character of each word is capitalized except for the first word.

• Pascal case: The first character of each word is capitalized including the first word.



### Creating JSON strings

JSON strings can be created in two ways, either from scratch or from a corresponding ABAP data structure. Using the XCO JSON data builder, JSON data can be built like

> ### Sample Code:  
> ```lang-abap
> DATA(lo_json_builder) = xco_cp_json=>data->builder( ).
> lo_json_builder->begin_object(
>   )->add_member( 'SessionId' )->add_string( '7cd44fff-036a-4155-b0d2-f5a4dfbcee92'
>   )->add_member( 'UserName' )->add_string( 'John Doe'
>   )->add_member( 'IsPremiumUser' )->add_boolean( abap_true
>   )->end_object( ).
> 
> " After execution LV_JSON_STRING will have the value
> " {"SessionId":"7cd44fff-036a-4155-b0d2-f5a4dfbcee92","UserName":"John Doe","IsPremiumUser":true}
> DATA(lv_json_string) = lo_json_builder->get_data( )->to_string( ).
> ```

In the same way that a JSON string can be translated to an appropriate ABAP data structure an ABAP data structure can be translated to a JSON string. It is again possible to apply transformations to e.g. transform underscore to camel case notation.

> ### Sample Code:  
> ```lang-abap
> TYPES:
>   BEGIN OF ts_output,
>     session_id      TYPE sysuuid_c36,
>     user_name       TYPE string,
>     is_premium_user TYPE xsdboolean,
>   END OF ts_output.
> 
> DATA(ls_output) = VALUE ts_output(
>   session_id      = '7cd44fff-036a-4155-b0d2-f5a4dfbcee92'
>   user_name       = |John Doe|
>   is_premium_user = abap_true
> ).
> 
> " After execution LV_JSON_STRING will have the value
> " {"SessionId":"7cd44fff-036a-4155-b0d2-f5a4dfbcee92","UserName":"John Doe","IsPremiumUser":true}
> DATA(lv_json_string) = xco_cp_json=>data->from_abap( ls_output )->apply( VALUE #(
>   ( xco_cp_json=>transformation->underscore_to_pascal_case )
> ) )->to_string( ).
> ```

