<!-- loio680f68b1c2fd4eb08de178a504fc6603 -->

# Currency Conversion

The ABAP Core Data Services \(CDS\) provide the built-in function `CURRENCY_CONVERSION` to convert different currencies to a common target currency.

For more information, see [CDS DDL - CDS View Entity, Unit and Currency Conversion Functions](https://help.sap.com/doc/abapdocu_cp_index_htm/CLOUD/en-US/index.htm?file=abencds_conv_func_unit_curr_v2.htm) in the [ABAP Keyword Documentation](https://help.sap.com/doc/abapdocu_cp_index_htm/CLOUD/en-US/index.htm).

To customize this conversion function, you can use API class `CL_EXCHANGE_RATES` to load the current exchange rates into your system for a correct conversion. Class `CL_EXCHANGE_RATES` is based on the business API function modules `BAPI_EXCHRATE_CREATEMULTIPLE` and `BAPI_EXCHANGERATE_SAVEREPLICA`.

API class `CL_EXCHANGE_RATES` provides PUT methods to write exchange rates to the corresponding customizing persistence. For more information, see the ABAP Doc comments in the class implementation.

Note that aside from use in CDS, the class additionally provides two methods to convert currencies.



<a name="loio680f68b1c2fd4eb08de178a504fc6603__section_d3l_bkd_jqb"/>

## Example

To learn how to obtain and store exchange rates from an official source, see the detailed example at [https://github.com/SAP-samples/cloud-abap-exchange-rates](https://github.com/SAP-samples/cloud-abap-exchange-rates).



> ### Sample Code:  
> ```abap
>  @EndUserText.label: 'Price (in US American Dollars)'
>   currency_conversion(
>     client => client,
>     amount => amount,
>     round => '',
>     source_currency => currency,
>     target_currency => cast('USD' as abap.cuky),
>     exchange_rate_type => cast('M' as abap.char(4)),
>     exchange_rate_date => cast($session.system_date as abap.dats)
>                      ) as PriceInUSD
> ```

