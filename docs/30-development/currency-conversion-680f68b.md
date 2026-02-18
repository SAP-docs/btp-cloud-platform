<!-- loio680f68b1c2fd4eb08de178a504fc6603 -->

# Currency Conversion

The ABAP Core Data Services \(CDS\) provide the built-in function `CURRENCY_CONVERSION` to convert different currencies to a common target currency.

For more information, see [CDS DDL - CDS View Entity, Unit and Currency Conversion Functions](https://help.sap.com/doc/abapdocu_cp_index_htm/CLOUD/en-US/index.htm?file=abencds_conv_func_unit_curr_v2.htm) in the [ABAP Keyword Documentation](https://help.sap.com/doc/abapdocu_cp_index_htm/CLOUD/en-US/index.htm).

To customize this conversion function, you can use API class `CL_EXCHANGE_RATES` to load the current exchange rates into your system for a correct conversion. Class `CL_EXCHANGE_RATES` is based on the business API function modules `BAPI_EXCHRATE_CREATEMULTIPLE` and `BAPI_EXCHANGERATE_SAVEREPLICA`.

API class `CL_EXCHANGE_RATES` provides PUT methods to write exchange rates to the corresponding customizing persistence. For more information, see the ABAP Doc comments in the class implementation.

Note that aside from use in CDS, the class additionally provides two methods to convert currencies.



<a name="loio680f68b1c2fd4eb08de178a504fc6603__section_d3l_bkd_jqb"/>

## Example



> ### Sample Code:  
> ```abap
>  @AccessControl.authorizationCheck: #NOT_REQUIRED
> @EndUserText.label: 'Currency Conversion Example'
> @Metadata.ignorePropagatedAnnotations: true
> define view entity Z_CURR_CONV_EXAMPLE 
> as select from /DMO/I_Supplement
> {
>   key SupplementID,
>       @Semantics.amount.currencyCode: 'CurrencyCode'
>       Price,
>       CurrencyCode,
>       @Semantics.amount.currencyCode: 'CurrencyUSD'
>       currency_conversion(
>                            amount => Price,
>                            round => '',
>                            source_currency => CurrencyCode,
>                            target_currency => cast('USD' as abap.cuky),
>                            exchange_rate_date => cast($session.system_date as abap.dats)
>                          ) as PriceInUSD,
>       cast('USD' as abap.cuky) as CurrencyUSD
> }
> 
> ```

> ### Note:  
> You can find a more detailed working example in GitHub at [https://github.com/SAP-samples/cloud-abap-exchange-rates](https://github.com/SAP-samples/cloud-abap-exchange-rates) to learn how to obtain and store exchange rates from an official source.

