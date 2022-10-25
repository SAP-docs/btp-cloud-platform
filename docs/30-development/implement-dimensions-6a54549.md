<!-- loio6a54549f13644fbd83c3312fef443036 -->

# Implement Dimensions

This part of the guide will show you how to implement dimensions needed for the [Star Schema](star-schema-483cc06.md).

You have created a data definition as described in [Create Data Definitions using CDS View Entities](create-data-definitions-using-cds-view-entities-c5f4dc1.md)

Dimension views provide additional attributes for the dimension fields in the cube view. See [Star Schema](star-schema-483cc06.md).

In order to avoid the generation of SQL artifacts that are not required by the analytical engine\(s\) to process the query, a new artifact type in CDS is introduced. This is the `transient (projection) view entity`. These transient view entities support the same functionality as other CDS entity types, with the main difference being that no SQL artifact is generated in the HANA database during activation. The basic CDS syntax looks as follows:

> ### Sample Code:  
> ```
> DEFINE TRANSIENT VIEW ENTITY <entity_name>
>     PROVIDER CONTRACT analytical_query
>     WITH PARAMETERS <param_name> : <param_type> DEFAULT <value>, …
>     AS PROJECTION ON <data_source_name>
> {
>       …
> } …;
> ```

Dimensions consist of several parts. These are:

1.  The mandatory header annotions for dimensions:

    ```abap
    @AbapCatalog.viewEnhancementCategory: [#NONE]
    @AccessControl.authorizationCheck: #NOT_REQUIRED
    @EndUserText.label: 'View entity agency'
    @Analytics.dataCategory: #DIMENSION
    @ObjectModel.representativeKey: 'AgencyId'
    ```

2.  The data source that you would like to select from, as well as associations.

    ```abap
    define view entity Z_VE_AGENCY_DIM
    as select from /dmo/agency as _Agency
    association to /DMO/I_Travel_U as _Travel on $projection.AgencyId = _Travel.AgencyID
    ```

3.  While defining the fields, 'as' must be used to define an alternative element name alias.

    **Fields Definition**

    ```abap
    key agency_id    as AgencyId,
     name             as Name,
     street           as Street,
     postal_code      as PostalCode,
     city             as City,
     country_code     as CountryCode,
     phone_number     as PhoneNumber,
      /* Associations */
     _Travel.TravelID as TravelID,
     _Travel
    ```




<a name="loio6a54549f13644fbd83c3312fef443036__section_npv_lbc_q4b"/>

## Result

**Z\_AIRLINE\_VE\_DIM**

```abap
@AbapCatalog.viewEnhancementCategory: [#NONE]
@AccessControl.authorizationCheck: #NOT_REQUIRED
@EndUserText.label: 'View entity agency'
@Analytics.dataCategory: #DIMENSION
@ObjectModel.representativeKey: 'AgencyId'
 
define view entity Z_VE_AGENCY_DIM
as select from /dmo/agency as _Agency
association to /DMO/I_Travel_U as _Travel on $projection.AgencyId = _Travel.AgencyID
{
 key agency_id    as AgencyId,
 name             as Name,
 street           as Street,
 postal_code      as PostalCode,
 city             as City,
 country_code     as CountryCode,
 phone_number     as PhoneNumber,
  /* Associations */
 _Travel.TravelID as TravelID,
 _Travel
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

**Z\_VE\_AIRLINE\_DIM**

```abap
@AbapCatalog.viewEnhancementCategory: [#NONE]
@AccessControl.authorizationCheck: #NOT_REQUIRED
@EndUserText.label: 'View entity for Airline'
@Analytics.dataCategory: #DIMENSION
@ObjectModel.representativeKey: 'CarrierId'
 
define view entity Z_VE_AIRLINE_DIM
as select from /dmo/carrier as _Airline
{
 
@ObjectModel.text.element: ['AirlineName']
key carrier_id    as CarrierId,
    name          as AirlineName,
    currency_code as CurrencyCode
 
}
```

**Z\_CONNECTION\_VE\_DIM**

```abap
@AbapCatalog.viewEnhancementCategory: [#NONE]
@AccessControl.authorizationCheck: #NOT_REQUIRED
@EndUserText.label: 'View entity connection'
@Analytics.dataCategory:  #DIMENSION
@ObjectModel.representativeKey: 'ConnectionId'
 
define view entity Z_VE_CONNECTION_DIM
as select from /dmo/connection as _Connection
 
association to Z_VE_AIRLINE_DIM as _Airline on $projection.CarrierId = _Airline.CarrierId
 
{
  @ObjectModel.foreignKey.association: '_Airline'
  key carrier_id    as CarrierId,
  key connection_id as ConnectionId,
  airport_from_id   as AirportFromId,
  airport_to_id     as AirportToId,
  departure_time    as DepartureTime,
  arrival_time      as ArrivalTime,
  distance          as Distance,
  distance_unit     as DistanceUnit, 
  concat(airport_from_id, airport_to_id) as trip,
    /* Associations */  
  _Airline 
}
```

**Z\_VE\_CUSTOMER\_DIM**

```abap
@AbapCatalog.viewEnhancementCategory: [#NONE]
@AccessControl.authorizationCheck: #CHECK
@EndUserText.label: 'View entity customer'
@Analytics.dataCategory: #DIMENSION
@ObjectModel.representativeKey: 'CustomerId'
 
define view entity Z_VE_CUSTOMER_DIM
as select from /dmo/customer as _Customer
association [0..1] to I_Country as _Country on $projection.CountryCode = _Country.Country
{
    key customer_id as CustomerId,
    first_name      as FirstName,
    last_name       as LastName,
    title           as Title,
    street          as Street,
    postal_code     as PostalCode,
    city            as City,
    @ObjectModel.foreignKey.association: '_Country'
    country_code    as CountryCode,
    /* Associations */
    _Country
}
```

