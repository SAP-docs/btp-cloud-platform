<!-- loioceb1a4ed90204501b19fe91be81dbf73 -->

# UUID



To effectively work with UUIDs the XCO standard library provides a simple way to translate between different UUID formats:

> ### Sample Code:  
> ```lang-abap
> DATA(lo_uuid) = xco_cp_uuid=>format->c36->to_uuid( '7cd44fff-036a-4155-b0d2-f5a4dfbcee92' ).
> 
> " LV_UUID_C32 will hold the value 7CD44FFF036A4155B0D2F5A4DFBCEE92
> DATA(lv_uuid_c32) =  CONV sysuuid_c32( xco_cp_uuid=>format->c32->from_uuid( lo_uuid ) ).
> ```

