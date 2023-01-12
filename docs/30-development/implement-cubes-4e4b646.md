<!-- loio4e4b646c8eba466a8238007869a7ae41 -->

# Implement Cubes

As we will be using associations and dimensions in our view, we will be implementing cube views instead of a fact views. The cube is the analytical interface view that is also used in the respective queries and holds the model together. It selects from facts and can be enriched with additional fields.

1.  Create another data definition as described in [Create Data Definitions using CDS View Entities](create-data-definitions-using-cds-view-entities-c5f4dc1.md).
2.  Add the mandatory header annotion for cubes:

    **Header Annotation**: `@Analytics.dataCategory: #CUBE`

3.  Choose the data source that you would like to select from.

    ```abap
    define view entity Z_VE_FLTBKS_CUBE
    as select from /DMO/I_Booking_U as _Booking
    ```

4.  An association is used to link a view \(or table\) to the source view \(or table\) in CDS Views entities. In an association, cardinality is defined. Cardinality is the relationship between the source and associated view entities in the form of \[ min .. max \]. Only the target cardinality is stated. The cardinality of associations in a cube has to be \[0..1\].

    **Associations**

    ```abap
    association to Z_VE_CUSTOMER_DIM        as _Customer   on  _Booking.CustomerID    = _Customer.CustomerId
      association to Z_VE_AIRLINE_DIM         as _Airline    on  _Booking.AirlineID     =  _Airline.CarrierId
      association to Z_VE_CONNECTION_DIM      as _Connection on  _Booking.AirlineID     = _Connection.CarrierId
                                                             and _Booking.ConnectionID  = _Connection.ConnectionId
      association to Z_VE_AGENCY_DIM          as _Agency     on  _Booking.TravelID      = _Agency.TravelID
      association to I_Currency               as _Currency      on _Currency.Currency = $projection.CurrencyCode
      association to /DMO/I_Travel_U          as _Travel     on _Booking.TravelID = _Travel.TravelID    
    ```

5.  All cubes must have at least one measure. For more information on measures, see [Star Schema](star-schema-483cc06.md).

    **Default aggregation**

    ```abap
    @Aggregation.default: #SUM
      1                     as  TotalNoOfBookings,
    ```

6.  Associations of external attributes are determined by foreign keys using annotation **@ObjectModel.foreignKey.association**. These are the links to the dimensions

    **Foreign key association**

    ```abap
      @ObjectModel.foreignKey.association: '_Customer'
      _Booking.CustomerID    as CustomerID,
    ```




<a name="loio4e4b646c8eba466a8238007869a7ae41__section_npv_lbc_q4b"/>

## Result

**Z\_VE\_FLTBKS\_CUBE**

```abap
@AbapCatalog.viewEnhancementCategory: [#NONE]
@AccessControl.authorizationCheck: #NOT_REQUIRED
@EndUserText.label: 'View entity flight bookings cube'
@Analytics.dataCategory: #CUBE
 
define view entity Z_VE_FLTBKS_CUBE
as select from /DMO/I_Booking_U as _Booking
  association to Z_VE_CUSTOMER_DIM        as _Customer   on  _Booking.CustomerID    = _Customer.CustomerId
  association to Z_VE_AIRLINE_DIM         as _Airline    on  _Booking.AirlineID     =  _Airline.CarrierId
  association to Z_VE_CONNECTION_DIM      as _Connection on  _Booking.AirlineID     = _Connection.CarrierId
                                                         and _Booking.ConnectionID  = _Connection.ConnectionId
  association to Z_VE_AGENCY_DIM          as _Agency     on  _Booking.TravelID      = _Agency.TravelID
  association to I_Currency               as _Currency      on _Currency.Currency = $projection.CurrencyCode
  association to /DMO/I_Travel_U          as _Travel     on _Booking.TravelID = _Travel.TravelID    
{
 
  key _Booking.TravelID  as TravelID,
  key _Booking.BookingID as BookingID ,
  @ObjectModel.foreignKey.association: '_Customer'
  _Booking.CustomerID    as CustomerID,
  @ObjectModel.foreignKey.association: '_Airline'
  _Booking.AirlineID     as Airline,
  @ObjectModel.foreignKey.association: '_Connection'
  _Booking.ConnectionID  as ConnectionID,
  _Booking.FlightDate    as FlightDate,
  _Booking.FlightPrice   as FlightPrice,
  _Booking.CurrencyCode  as CurrencyCode,
  _Connection.Distance   as Distance,
  _Connection.DistanceUnit as DistanceUnit, 
  _Travel.BookingFee as BookingFee,
  _Travel.TotalPrice as TotalPrice,
   
  @Semantics.amount.currencyCode: 'CurrencyCode'
  _Booking.FlightPrice + _Travel.BookingFee             as FlightPricePerBooking,
   
  _Booking.BookingDate   as BookingDate,
   
  @Aggregation.default: #SUM
  1                     as  TotalNoOfBookings,
    /* Associations */
_Customer,
_Airline,
_Connection,
_Agency,
_Currency,
_Travel
}
```



### Important Notes:

-   It isn't mandatory to construct a fact view to consume it from a cube; you can expose the table that holds the measures directly in the cube view to avoid an extra view and consequently an unnecessary level. Fact views cannot have joins or associations and they must hold only measurable values. If you want to connect your dimensions in the same view you should use a cube view instead of a fact view.
-   All cubes must have an `@Analytics.dataCategory: #CUBE` classification in the header of the view.
-   Associations of external attributes are determined by foreign keys using annotation `@ObjectModel.foreignKey.association`.
-   The `@Aggregation.default` annotation should be placed before the fields determined as **measures**.
-   The annotation **@Semantics** helps to define the currency and quantity.



<a name="loio4e4b646c8eba466a8238007869a7ae41__section_q4b_gyp_w5b"/>

## The other cube required for our example

> ### Sample Code:  
> ```
> @AbapCatalog.viewEnhancementCategory: [#NONE]
> @AccessControl.authorizationCheck: #NOT_REQUIRED
> @EndUserText.label: 'Flight Cube'
> @Analytics.dataCategory: #CUBE
> define view entity Z_VE_Flight_Cube
>   as select from /DMO/I_Flight_R as _Flight
>   association to Z_VE_AIRLINE_DIM as _Carrier on _Flight.AirlineID = _Carrier.CarrierId
> {
>       @ObjectModel.foreignKey.association: '_Carrier'
>   key AirlineID,
>   key ConnectionID,
>   key FlightDate,
>       Price,
>       CurrencyCode,
>       PlaneType,
>       MaximumSeats,
>       OccupiedSeats,
>       @Aggregation.default: #MIN
>       MaximumSeats - OccupiedSeats as TotalFreeSeats,
>       /* Associations */
>       _Carrier
>  
> }
> ```

