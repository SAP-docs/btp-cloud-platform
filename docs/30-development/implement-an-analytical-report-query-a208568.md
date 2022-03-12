<!-- loioa208568685a2448abd4b9081e80c8f00 -->

# Implement an Analytical Report \(Query\)

Follow these steps to implement a query on top of your analytical model.

For more information, see [Query](query-d3f8dc9.md).

You have completed the following steps:

-   [Implement Dimensions](implement-dimensions-6a54549.md)
-   [Implement a Cube](implement-a-cube-4e4b646.md)

1.  Create another data definition as described in [Create Data Definitions using CDS View Entities](create-data-definitions-using-cds-view-entities-c5f4dc1.md).
2.  Add the mandatory header annotion for queries:

    **Header Annotation**: `@Analytics.query: true`

3.  Choose the data source that you would like to select from.

    ```abap
    define view entity Z_BOOKINGS_VE_QUERY
      as select from Z_BOOKINGS_VE_CUBE as BookingsCube
    ```

4.  Add the query annotations:

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




<a name="loioa208568685a2448abd4b9081e80c8f00__section_vns_vfc_q4b"/>

## Result

**Z\_Bookings\_VE\_Query**

```abap
@EndUserText.label: 'Bookings View Entity - CDS Data Model'
@Analytics.query: true
 
define view entity Z_BOOKINGS_VE_QUERY
  as select from Z_BOOKINGS_VE_CUBE as BookingsCube
 
{
      /*Dimensions*/    
      @AnalyticsDetails.query.display: #KEY_TEXT
      @AnalyticsDetails.query.axis: #ROWS
  key BookingsCube.TravelID,
      @AnalyticsDetails.query.display: #KEY_TEXT
      @AnalyticsDetails.query.axis: #ROWS
  key BookingsCube.BookingID,
      @AnalyticsDetails.query.axis: #ROWS
      BookingsCube.BookingDate,
      @AnalyticsDetails.query.axis: #ROWS
      BookingsCube.CustomerID,
      @AnalyticsDetails.query.axis: #ROWS
      BookingsCube.AirlineID,
      @AnalyticsDetails.query.axis: #ROWS
      BookingsCube.CustomerCountry,
      @AnalyticsDetails.query.axis: #ROWS
      BookingsCube.CustomerCity,
      @AnalyticsDetails.query.axis: #ROWS
      BookingsCube.ConnectionID,
      @AnalyticsDetails.query.axis: #ROWS
      BookingsCube.CurrencyCode,
      @AnalyticsDetails.query.axis: #ROWS
      BookingsCube.FlightDate,
      @AnalyticsDetails.query.axis: #ROWS
      BookingsCube.AgencyID,
      @AnalyticsDetails.query.axis: #ROWS
      BookingsCube.AgencyName,
 
      /*Measures*/
      TotalOfBookings,
      FlightPrice   
}
```

**Related Information**  


[Star Schema](star-schema-483cc06.md "The structure of the analytical model resembles a star (see graphic below): The cube or fact view at its center is surrounded by and connected to various dimension views. That's why it is also referred to as a star schema.")

[Query](query-d3f8dc9.md "")

