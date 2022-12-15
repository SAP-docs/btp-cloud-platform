<!-- loioa208568685a2448abd4b9081e80c8f00 -->

# Implement an Analytical Report \(Query\)

Follow these steps to implement a query on top of your analytical model.

For more information, see [Analytical Query](analytical-query-d3f8dc9.md).

**Prerequisites:**

You have completed the following steps:

-   [Implement Dimensions](implement-dimensions-6a54549.md)
-   [Implement Cubes](implement-cubes-4e4b646.md)

1.  Create another data definition as described in [Create Data Definitions using CDS View Entities](create-data-definitions-using-cds-view-entities-c5f4dc1.md).
2.  Choose the underlying cube view.

    ```
    DEFINE TRANSIENT VIEW ENTITY <entity_name>
        PROVIDER CONTRACT analytical_query
        WITH PARAMETERS <param_name> : <param_type> DEFAULT <value>, …
        AS PROJECTION ON <data_source_name>
    {
          …
    } …;
    ```

3.  Add the query annotations:

    -   Annotation `@AnalyticsDetails.query.axis:'<VALUE>’` 

        **Description**: Position elements of a view on a speciﬁc axis.

        **Possible values**: FREE, ROWS or COLUMNS.

        With the annotation `@AnalyticsDetails.query.axis`, the elements of the view can be positioned on multiple axes. The elements can be directly annotated with their axis. All measures \(elements which can be aggregated\) need to be on the same axis. The annotation of the first measure will therefore be used for all measures of the query. If `@AnalyticsDetails.query.axis` is not found, the system positions the measures on the columns. The default value for elements that are not measures is the free axis. Note that elements in the projection list which belong to the same ﬁeld in the query will be grouped together.

    -   Annotation `@AnalyticsDetails.query.display: #KEY_TEXT` is used to display the text of the key.


    For more information on all the different query annotations, see [AnalyticsDetails Annotations](https://help.sap.com/viewer/923180ddb98240829d935862025004d6/Cloud/en-US/362d98c100ed4497aead426b72a64e16.html).

     **Query Annotations**

    ```abap
        @AnalyticsDetails.query.display: #KEY_TEXT
        @AnalyticsDetails.query.axis: #ROWS
    key BookingsCube.TravelID,
    ```






### Analytical Report 1

 **Z\_VE\_ANA\_PROJVIEW\_Q** 

```
@EndUserText.label: 'Analytical projection view'
@AccessControl.authorizationCheck: #NOT_ALLOWED                          // No definition of a DCL
define transient view entity Z_VE_ANA_PROJVIEW_Q                         // transient: only a ABAP Server runtime object is generated
  provider contract analytical_query                                     // provider contract analytical query: strict analytical checks are executed inside Dictionary Activation
   
  with parameters                                                        // Parameters are allowed
    p_preferred_currency : abap.dec(15,2)
 
  as projection on Z_VE_FLTBKS_CUBE                                      // Underlying View needs to be a CUBE view
{
 
          @AnalyticsDetails.query.axis: #ROWS
          TravelID,
          @AnalyticsDetails.query.axis: #ROWS
          BookingID,
          @AnalyticsDetails.query.axis: #ROWS
          CustomerID,
          @AnalyticsDetails.query.axis: #ROWS
          Airline,
          @AnalyticsDetails.query.axis: #ROWS
          ConnectionID,
          @AnalyticsDetails.query.axis: #ROWS
          FlightDate,
          @AnalyticsDetails.query.axis: #ROWS
          FlightPrice,
          @AnalyticsDetails.query.axis: #ROWS
          CurrencyCode,
          @AnalyticsDetails.query.axis: #ROWS
          BookingDate,
          TotalNoOfBookings,
          @AnalyticsDetails.query.axis: #ROWS
          Distance,
          @AnalyticsDetails.query.axis: #ROWS
          DistanceUnit,
          @AnalyticsDetails.query.axis: #ROWS
          TotalPrice,
          @AnalyticsDetails.query.axis: #ROWS
          BookingFee,
          @AnalyticsDetails.query.axis: #ROWS
          FlightPricePerBooking,         
           
          @AnalyticsDetails.query.axis: #ROWS                               // Typed Literals
          @Aggregation.default: #FORMULA                                    // Calculated Units as references for calculated quantities
          @EndUserText.label: 'Discount On Booking'
          abap.decfloat34'0.05'                                  as DiscountOnBooking,
 
          @AnalyticsDetails.query.axis: #ROWS
          @Aggregation.default: #FORMULA
          @EndUserText.label: 'Tax On Booking'
          abap.decfloat34'0.19'                                  as TaxOnBooking,
 
          @AnalyticsDetails.query.axis: #ROWS
  virtual CurrencyCode1 : abap.cuky( 5 ),                                   // Definition of calculated units via virtual   
 
          @AnalyticsDetails.query.axis: #ROWS
          @Semantics.amount.currencyCode: 'CurrencyCode1'
          @Aggregation.default: #FORMULA
          @EndUserText.label: 'FliPrice Discounted'
          curr_to_decfloat_amount( FlightPricePerBooking ) * ( 1 - $projection.DiscountOnBooking  ) as FlightPriceDiscounted, // Referring to other expressions via $projection
          
          @AnalyticsDetails.query.axis: #ROWS
          @Semantics.amount.currencyCode: 'CurrencyCode'
          @Aggregation.default: #FORMULA
          @EndUserText.label: 'Final Flight Price'
          $projection.FlightPriceDiscounted * ( 1 + $projection.TaxOnBooking )                      as FlightPriceDiscountedTaxed
           
}
```



### Analytical Report 2

For our example, we will be using two queries. Copy following is the code needed for the second query.

> ### Sample Code:  
> ```
> @AbapCatalog.viewEnhancementCategory: [#NONE]
> @AccessControl.authorizationCheck: #NOT_ALLOWED
> @EndUserText.label: 'Flight Analytical Projection Query'
> define transient view entity Z_VE_Flight_AnaProj_Query
>   provider contract analytical_query 
>   
>   as projection on Z_VE_Flight_Cube
> {
>     @AnalyticsDetails.query.axis: #ROWS
>     AirlineID,
>     @AnalyticsDetails.query.axis: #ROWS
>     ConnectionID,
>     @AnalyticsDetails.query.axis: #ROWS
>     FlightDate,
>     @AnalyticsDetails.query.axis: #ROWS
>     Price,
>     @AnalyticsDetails.query.axis: #ROWS
>     CurrencyCode,
>     @AnalyticsDetails.query.axis: #ROWS
>     PlaneType,
>     @AnalyticsDetails.query.axis: #ROWS
>     MaximumSeats,
>     @AnalyticsDetails.query.axis: #ROWS
>     OccupiedSeats,
>     @AnalyticsDetails.query.axis: #ROWS
>     TotalFreeSeats    
> }
> ```

**Related Information**  


[Star Schema](star-schema-483cc06.md "The structure of the analytical model resembles a star (see graphic below): The cube or fact view at its center is surrounded by and connected to various dimension views. That's why it is also referred to as a star schema.")

[Analytical Query](analytical-query-d3f8dc9.md "")

