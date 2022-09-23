<!-- loioa69e99c457a54ff881adcff843eea950 -->

# Service Consumption Model as RFC Consumer

Instead of using the `CALL FUNCTION ... DESTINATION` statement, you can configure an RFC connection with a Service Consumption Model \(SRVC\).



<a name="loioa69e99c457a54ff881adcff843eea950__section_byf_hlz_qsb"/>

## Concept

Based on tool support in ABAP Development Tools \(ADT\), you can generate an ABAP proxy for calling one or more remote-enabled function modules \(RFMs\) using the SRVC.

The proxy class contains a specific method for each called RFM. The main benefit of using an SRVC for RFC is that in this class, all data types required for the RFM parameters are generated automatically.

The best way to define an RFC proxy class is to use it for calling only one RFM, or a few RFMs that belong together semantically.

For more information on generating an RFC proxy class based on an SRVC, see [Generating Proxies for Remote Function Call \(RFC\)](https://help.sap.com/docs/BTP/5371047f1273405bb46725a417f95433/32812d950d3848359ce391dae477f201.html?version=Cloud).

In ADT, you can find an example code snippet in the SRVC object of the corresponding RFM.



<a name="loioa69e99c457a54ff881adcff843eea950__section_mlp_xlz_qsb"/>

## Advantages

In many cases, you can reduce development efforts for synchronous RFC calls to other systems significantly by generating an RFC proxy via the SRVC.

The SRVC generates data types required for a typed access to the RFC response.

When using the `CALL FUNCTION ... DESTINATION` statement in these cases, you would have to generate all affected data types manually.

The effort increases with the number and complexity of the required data types. For example, in ABAP applications containing tables with a large number of columns, manual data type generation would be time-consuming. This effort is reduced significantly when using an SRVC.

You can save even more time if you're calling the same RFM in different releases and some of the required data types have different characteristics in each release. In this case, you wouldn't only have to generate the different data types for each release separately, but also in different versions. Note that for each release, one proxy is required.

You can also benefit from RFC calls via SRVC if you want to perform object-oriented development in a consistent manner.

