<!-- loio6a54549f13644fbd83c3312fef443036 -->

# Implement Dimensions

You have created a data definition as described in [Create Data Definitions using CDS View Entities](Create_Data_Definitions_using_CDS_View_Entities_c5f4dc1.md). Now follow these steps to create dimensions.

Dimension views provide additional attributes for the dimension fields in the cube view. See [Star Schema](Star_Schema_483cc06.md).

1.  Add the mandatory header annotions for dimensions:

    ```lang-abap
    @Analytics.dataCategory: #DIMENSION
    @ObjectModel.representativeKey: 'CarrierID'
    ```

2.  Choose the data source that you would like to select from.

    ```lang-abap
    define view entity Z_AIRLINE_VE_DIM
      as select from /dmo/carrier as Airline
    ```

3.  While defining the fields, 'as' must be used to define an alternative element name alias.

    **Fields Definition**

    ```lang-abap
    key   Airline.carrier_id    as CarrierId,
          Airline.name          as AirlineName,     
          Airline.currency_code as CurrencyCode
    ```

4.  Field annotations must be defined on top of the fields.

    **Fields Annotations**

    ```lang-abap
     @ObjectModel.text.element: ['AirlineName']
    key Airline.carrier_id    as CarrierId,
     
        @Semantics.text: true
        @Search.defaultSearchElement: true
        @Search.fuzzinessThreshold: 0.7
        Airline.name          as AirlineName,
         
        Airline.currency_code as CurrencyCode
    ```

    The fields are prefixed with the alias of the data source name. This is to avoid duplication of field names when multiple data sources are used.

    **Prefixed field with data source alias**

    ```
     Airline.name          as AirlineName
    ```




<a name="loio6a54549f13644fbd83c3312fef443036__section_npv_lbc_q4b"/>

## Result

**Z\_AIRLINE\_VE\_DIM**

```lang-abap
@AbapCatalog.viewEnhancementCategory: [#NONE]
@AccessControl.authorizationCheck: #CHECK
@EndUserText.label: 'Airline View Entity - CDS Data Model'
@ObjectModel.usageType:{
    serviceQuality: #X,
    sizeCategory: #S,
    dataClass: #MIXED
}
 
@Analytics.dataCategory: #DIMENSION
@ObjectModel.representativeKey: 'CarrierId'
 
define view entity Z_AIRLINE_VE_DIM
  as select from /dmo/carrier as Airline
 
{
      @ObjectModel.text.element: ['AirlineName']
  key Airline.carrier_id    as CarrierId,
 
      @Semantics.text: true
      @Search.defaultSearchElement: true
      @Search.fuzzinessThreshold: 0.7
      Airline.name          as AirlineName,
       
      Airline.currency_code as CurrencyCode
} 
```



### Important Notes:

-   All dimensions must have an `@Analytics.dataCategory: #DIMENSION` classification in the header of the view entity.
-   A correlation of a field with its descriptive language-independent texts and names are established through annotation `@ObjectModel.text.element`. For language-dependent texts, a view of type `@ObjectModel.dataCategory: #TEXT` is needed. This view would then be associated via annotation `@ObjectModel.text.association`.
-   Associations of external attributes are determined by foreign keys using annotation **@ObjectModel.foreignKey.association**.
-   Dimensions with composite keys need a definition of a single field as a representative key. This configuration is achieved through annotation **@ObjectModel.representativeKey**. The representative key is a key field. If there are multiple key fields, it points to the most specific one.
-   Annotation `@Semantics` helps to specify the semantic of a field e.g., text/calendar date/unit/amount.

For more information on the annotations, see [CDS Annotations](https://help.sap.com/viewer/923180ddb98240829d935862025004d6/Cloud/en-US/130e02a697e14bf8b05dd6672c56250b.html).



### Other dimensions needed for our example:

**Z\_CUSTOMER\_VE\_DIM**

```lang-abap
@AbapCatalog.viewEnhancementCategory: [#NONE]
@AccessControl.authorizationCheck: #CHECK
@EndUserText.label: 'Customer View Entity - CDS View Model'
@ObjectModel.usageType:{
    serviceQuality: #X,
    sizeCategory: #S,
    dataClass: #MIXED
}
 
@Analytics.dataCategory: #DIMENSION
@ObjectModel.representativeKey: 'CustomerID'
 
define view entity Z_CUSTOMER_VE_DIM
as select from /dmo/customer as Customer
 
association [1] to I_Country as _Country on Customer.country_code = _Country.Country
 
{
   key Customer.customer_id  as CustomerId,
       Customer.first_name   as FirstName,
       Customer.last_name    as LastName,
       Customer.title        as Title,
       Customer.street       as Street,
       Customer.postal_code  as PostalCode,
       Customer.city         as City,
       @ObjectModel.foreignKey.association: '_Country'
       Customer.country_code as CountryCode,
       Customer.phone_number as PhoneNumber,
    
   /*Associations*/
   _Country
}
```

**Z\_CONNECTION\_VE\_DIM**

```lang-abap
@AbapCatalog.viewEnhancementCategory: [#NONE]
@AccessControl.authorizationCheck: #CHECK
@EndUserText.label: 'Connection View Entity - CDS View Model'
@ObjectModel.usageType:{
    serviceQuality: #X,
    sizeCategory: #S,
    dataClass: #MIXED
}
 
@Analytics.dataCategory: #DIMENSION
@ObjectModel.representativeKey: 'ConnectionID'
 
define view entity Z_Connection_VE_DIM
as select from /dmo/connection as Connection
association [1] to Z_AIRLINE_VE_DIM as _Airline on Connection.carrier_id = _Airline.CarrierId
 
{     @ObjectModel.foreignKey.association: '_Airline'
  key Connection.carrier_id      as CarrierId,
  key Connection.connection_id   as ConnectionId,
      Connection.airport_from_id as AirportFromId,
      Connection.airport_to_id   as AirportToId,
      Connection.departure_time  as DepartureTime,
      Connection.arrival_time    as ArrivalTime,
      Connection.distance        as Distance,
      Connection.distance_unit   as DistanceUnit,
      concat(airport_from_id, concat(' -> ', airport_to_id)) as Trip,
       
      /*Associations*/
      _Airline
}
```

**Z\_Agency\_VE\_DIM**

```lang-abap
@AbapCatalog.viewEnhancementCategory: [#NONE]
@AccessControl.authorizationCheck: #CHECK
@EndUserText.label: 'Agency View - CDS View Entity Model'
@ObjectModel.usageType:{
    serviceQuality: #X,
    sizeCategory: #S,
    dataClass: #MIXED
}
 
@Analytics.dataCategory: #DIMENSION
@ObjectModel.representativeKey: 'AgencyID'
 
define view entity Z_AGENCY_VE_DIM
as select from /dmo/agency as Agency
association to /DMO/I_Travel_U as _Travel  on Agency.agency_id = _Travel.AgencyID
 
{
   key agency_id       as AgencyId,
   @Semantics.text: true
   name                as Name,
   street              as Street,
   postal_code         as PostalCode,
   city                as City,
   country_code        as CountryCode,
   phone_number        as PhoneNumber,
   _Travel.TravelID    as TravelID,
     
   /*Associations*/
   _Travel
}
```

