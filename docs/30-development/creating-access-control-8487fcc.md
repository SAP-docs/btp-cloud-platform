<!-- loio8487fcc6b37c43c7a39400d5d5fc9351 -->

# Creating Access Control

To make sure that no unauthorized users access data, create access control for your CDS views.



## Context

In the example used in this documentation, you create two access controls – one for each view – and use the `aspect pfcg_auth` clause to access the region field in the authorization object. For the sake of simplicity, we don’t check the activity, that is, every activity is valid to view the records of a region.



## Procedure

1.  Create the following access controls:

    > ### Sample Code:  
    > ```abap
    > @EndUserText.label: 'ORDERS DCL'
    > @MappingRole: true
    > define role ZORDERSVIEW_DCL {
    >   grant 
    >     select
    >       on
    >         ZORDERSVIEW
    >           where
    >              (region) = aspect pfcg_auth(ZREGIONMGT, ZREGION);
    >             
    > }
    > 
    > ```

    > ### Sample Code:  
    > ```abap
    > @EndUserText.label: 'ORDER ITEMS DCL'
    > @MappingRole: true
    > define role ZORDERITEMSVIEW_DCL {
    >   grant 
    >     select
    >       on
    >         ZORDERITEMSVIEW
    >           where
    >             (_order.region) = aspect pfcg_auth(ZREGIONMGT, ZREGION);
    >                         
    > }
    > 
    > ```

    In the second access control, you use the `_order` association to get access to the order’s region field.


