<!-- loio4e4b646c8eba466a8238007869a7ae41 -->

# Implement a Cube

As we will be using associations and dimensions in our view, we will be implementing a cube view instead of a fact view. The cube is the analytical interface view that is also used in the respective queries and holds the model together. It selects from facts and can be enriched with additional fields.

1.  Create another data definition as described in [Create Data Definitions using CDS View Entities](Create_Data_Definitions_using_CDS_View_Entities_c5f4dc1.md).
2.  Add the mandatory header annotion for cubes:

    **Header Annotation**: `@Analytics.dataCategory: #CUBE`

3.  Choose the data source that you would like to select from.

    ```lang-abap
    define view entity Z_BOOKINGS_VE_CUBE
      as select from /DMO/I_Booking_U as Booking
    ```

4.  An association is used to link a view \(or table\) to the source view \(or table\) in CDS Views entities. In an association, cardinality is defined. Cardinality is the relationship between the source and associated view entities in the form of \[ min .. max \]. Only the target cardinality is stated. The cardinality of associations in a cube has to be \[0..1\].

    **Associations**

    ```lang-abap
    association [0..1] to Z_CUSTOMER_VE_DIM   as _Customer   on  Booking.CustomerID = _Customer.CustomerId
    association [0..1] to Z_AIRLINE_VE_DIM    as _Airline    on  Booking.AirlineID = _Airline.CarrierId
    association [0..1] to Z_Connection_VE_DIM as _Connection on  Booking.AirlineID    = _Connection.CarrierId
                                                      and Booking.ConnectionID = _Connection.ConnectionId
    association [0..1] to Z_AGENCY_VE_DIM     as _Agency     on  Booking.TravelID = _Agency.TravelID
    ```

5.  All cubes must have at least one measure. For more information on measures, see [Star Schema](Star_Schema_483cc06.md).

    **Default aggregation**

    ```lang-abap
    @EndUserText.label: 'Air Fare'
          @Semantics.amount.currencyCode: 'CurrencyCode'
          @Aggregation.default: #MIN
          Booking.FlightPrice   as FlightPrice,
    ```

6.  Associations of external attributes are determined by foreign keys using annotation **@ObjectModel.foreignKey.association**. These are the links to the dimensions

    **Foreign key association**

    ```lang-abap
    @ObjectModel.foreignKey.association: '_Airline'
    Booking.carrier_id             as AirlineID,
    ```




<a name="loio4e4b646c8eba466a8238007869a7ae41__section_npv_lbc_q4b"/>

## Result

**Z\_BOOKINGS\_VE\_CUBE**

```lang-abap
@AbapCatalog.viewEnhancementCategory: [#NONE]
@AccessControl.authorizationCheck: #CHECK
@EndUserText.label: 'Bookings view entity - CDS Data Model'
@Metadata.ignorePropagatedAnnotations: true
 
@Analytics.dataCategory: #CUBE
 
/*+[hideWarning] { "IDS" : [ "CARDINALITY_CHECK" ]  } */
define view entity Z_BOOKINGS_VE_CUBE
  as select from /DMO/I_Booking_U as Booking
 
  association [0..1] to Z_CUSTOMER_VE_DIM   as _Customer   on  Booking.CustomerID = _Customer.CustomerId
  association [0..1] to Z_AIRLINE_VE_DIM    as _Airline    on  Booking.AirlineID = _Airline.CarrierId
  association [0..1] to Z_Connection_VE_DIM as _Connection on  Booking.AirlineID    = _Connection.CarrierId
                                                    and Booking.ConnectionID = _Connection.ConnectionId
  association [0..1] to Z_AGENCY_VE_DIM     as _Agency     on  Booking.TravelID = _Agency.TravelID
 
{
      /* Dimensions */
  key Booking.TravelID      as TravelID,
 
  key Booking.BookingID     as BookingID,
 
      Booking.BookingDate   as BookingDate,
 
      @ObjectModel.foreignKey.association: '_Customer'
      Booking.CustomerID    as CustomerID,
 
      @ObjectModel.foreignKey.association: '_Airline'
      Booking.AirlineID     as AirlineID,
 
      @EndUserText.label: 'Customer Country'
      @ObjectModel.foreignKey.association: '_CustomerCountry'
      _Customer.CountryCode as CustomerCountry,
 
      @EndUserText.label: 'Customer City'
      _Customer.City        as CustomerCity,
 
      @ObjectModel.foreignKey.association: '_Connection'
      Booking.ConnectionID  as ConnectionID,
 
      // @Semantics.currencyCode: true
      Booking.CurrencyCode  as CurrencyCode,
 
      Booking.FlightDate    as FlightDate,
 
      _Agency.AgencyId      as AgencyID,
 
      _Agency.Name          as AgencyName,
 
      /* Measures */
 
      @EndUserText.label: 'Total of Bookings'
      @Aggregation.default: #SUM
      1           as TotalOfBookings,

      @EndUserText.label: 'Air Fare'
      @Semantics.amount.currencyCode: 'CurrencyCode'
      @Aggregation.default: #MIN
      Booking.FlightPrice   as FlightPrice,
 
 
      /* Associations */
      _Customer,
      _Airline,
      _Connection,
      _Customer._Country    as _CustomerCountry
 
}
```



### Important Notes:

-   It isn't mandatory to construct a fact view to consume it from inside of a cube; you can expose the table that holds the measures directly in the cube view to avoid an extra view and consequently an unnecessary level. Fact views cannot have joins or associations and they must hold only measurable values. If you want to connect your dimensions in the same view you should use a cube view instead of a fact view.
-   All cubes must have an `@Analytics.dataCategory: #CUBE` classification in the header of the view.
-   Associations of external attributes are determined by foreign keys using annotation `@ObjectModel.foreignKey.association`.
-   The `@Aggregation.default` annotation should be placed before the fields determined as **measures**.
-   The annotation **@Semantics** helps to define the currency and quantity.

