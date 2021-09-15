<!-- loio0c9b60f19d1644dabd4e89ebff79328d -->

# Generate a Proxy to Consume Remote-Enabled Function Modules

Generate an RFC proxy via the service consumption model.

In many cases, you can reduce development efforts for synchronous RFC calls to other systems significantly by generating an RFC proxy via the *service consumption model* \(SCM\), instead of using the standard *CALL FUNCTION* statement.

You can benefit from using RFC via proxy in particular if the data types of the parameters for an RFC call are not available on the client side.



<a name="loio0c9b60f19d1644dabd4e89ebff79328d__section_rjh_ncs_4qb"/>

## Concept

Based on tool support in *ABAP Development Tools* \(ADT\), you can generate an ABAP proxy for calling one or more remote-enabled functions modules \(RFMs\) using the SCM.

The proxy class contains a specific method for each called RFM. The main benefit of using SCM for RFC is that in this class, all data types required for the RFM parameters are generated automatically.

The best way to define an RFC proxy class is to use it for calling only one RFM, or few RFMs that belong together semantically.

In ADT, you can find an example code snippet in the SCM object of the corresponding RFM .



<a name="loio0c9b60f19d1644dabd4e89ebff79328d__section_jcj_ycs_4qb"/>

## Advantages

When developing your own RFM calls, you can benefit from a client-side ABAP proxy in particular if:

-   The called RFMs do not exist on the client side, and therefore the data types of the corresponding RFC parameters are not available on the client side.

-   The corresponding data types are available on the client side, but not part of the ABAP *language version 5* \(ABAP for cloud development\). Therefore, you must not use them in the respective systems for your custom development.

    For more information on ABAP language versions, see [ABAP Keyword Documentation](https://help.sap.com/doc/abapdocu_cp_index_htm/CLOUD/en-US/abenabap_versions.htm).


When using the *CALL FUNCTION* statement in these cases, you would have to generate all affected data types manually.

The effort increases with the number and complexity of the required data types. For example, in ABAP applications containing tables with a large number of columns, manual data type generation would be time-consuming. This effort is reduced significantly when using SCM.

You can save even more time if you are calling the same RFM in different releases and some of the required data types have different characteristics in each release. In this case, you would not only have to generate the different data types for each release separately, but also in different versions.

You can also benefit from RFC calls via proxy class if you want to perform object-oriented development in a consistent manner.



<a name="loio0c9b60f19d1644dabd4e89ebff79328d__section_x1p_lcs_4qb"/>

## For which RFC Calls Can You Generate an RFC Proxy via SCM?

You can generate a proxy for all RFC calls that are allowed for custom development in SAP BTP, ABAP environment and S/4HANA Cloud, ABAP environment according to*language version 5*. Currently, this includes all synchronous RFC calls.



<a name="loio0c9b60f19d1644dabd4e89ebff79328d__section_rvm_rls_4qb"/>

## Related Information

For information on how to generate an RFC proxy class based on an XML file and how to get this XML file, see:

[Generating Proxies for Remote Function Call \(RFC\)](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/32812d950d3848359ce391dae477f201.html) \(ADT documentation\)

