<!-- loio3a893d98029b429da160ac133a9f7232 -->

# Enhanced WSDL Document

The enhanced Web Services Description Language \(WSDL\) document is a WSDL document enhanced by ABAP information that is relevant for design time.

When you use a regular WSDL as input to create a Service Consumption Model \(SRVC\), the design time relevant information, such as the types, messages, and port type sections, are analyzed and interpreted by the ABAP Web service framework. For all the ABAP properties like the names and types, it will make suggestions and generate a WSDL similar to the input WSDL enhanced with this ABAP information. If needed, you can change these ABAP properties within the enhanced WSDL document to adjust the ABAP artifacts accordingly \(upon activation\). The mapping between XSD and ABAP types in particular can be adjusted this way. Of course, an enhanced WSDL document can be used as input as well.

To encode ABAP properties into the WSDL, the namespace `http://sap.com/abap/proxy` with the prefix `abap` was introduced: `xmlns:abap=http://sap.com/abap/proxy`. For any applicable node of a WSDL, the corresponding enhanced WSDL document contains additional nodes within this namespace to accommodate its ABAP properties. Wherever you see the `abap` prefix in the WSDL, you can adjust the ABAP property. These additional nodes can be XSD attributes or elements, depending on where the node to be enhanced is located. This is necessary to maintain WSDL validity. Schema nodes such as `xmlns:xsd=http://www.w3.org/2001/XMLSchema` are enhanced via additional XSD attributes. WSDL nodes `xmlns:wsdl=http://schemas.xmlsoap.org/wsdl/`, on the other hand, are enhanced via additional XSD \(sub\)elements. Regular ABAP properties of any node contain the following:

-   Prefix
-   Name
-   Description
-   ABAP type

With the ABAP type, you can control the mapping between XSD and ABAP types. The property `availableTypes` displays all applicable ABAP types in this case. To change the ABAP type, copy and paste one of the listed types into the type attribute of the given element. Afterwards, reactivate the SRVC to apply the changes.

**Summary of Additional Nodes and Their Technical Types**


<table>
<tr>
<th valign="top">

Node name

</th>
<th valign="top">

Technical Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`abap:prefix`

</td>
<td valign="top">

Up to 20 characters, case insensitive

</td>
<td valign="top">

ABAP prefix \(only used if the object is represented by an ABAP object such as `CLAS`, `INTF`, `TABL`, `DTEL`\)

</td>
</tr>
<tr>
<td valign="top">

`abap:name`

</td>
<td valign="top">

Up to 30 characters, case insensitive

</td>
<td valign="top">

ABAP name

</td>
</tr>
<tr>
<td valign="top">

`abap:type`

</td>
<td valign="top">

String

</td>
<td valign="top">

Default or set ABAP type

</td>
</tr>
<tr>
<td valign="top">

`abap:availableTypes`

</td>
<td valign="top">

Comma-separated list of 30 characters

</td>
<td valign="top">

List of all available ABAP types

</td>
</tr>
<tr>
<td valign="top">

`abap:description`

</td>
<td valign="top">

Up to 60 characters

</td>
<td valign="top">

Description

</td>
</tr>
<tr>
<td valign="top">

`abap:prefixT`

</td>
<td valign="top">

See `abap:prefix`

</td>
<td valign="top">

Prefix for corresponding table type \(if `maxOccurs` \> 1 and additional table type is generated and a prefix is required\)

</td>
</tr>
<tr>
<td valign="top">

`abap:nameT`

</td>
<td valign="top">

See `abap:name`

</td>
<td valign="top">

Name for corresponding table type \(if `maxOccurs` \> 1 and additional table type is generated\)

</td>
</tr>
<tr>
<td valign="top">

`abap:descriptionT`

</td>
<td valign="top">

See `abap:description`

</td>
<td valign="top">

Description for corresponding table type \(if maxOccurs \> 1 and additional table type is generated\)

</td>
</tr>
</table>

> ### Example:  
> The following code snippet displays a types section of an enhanced WSDL with a schema node \(prefix `xsd`\), where all ABAP properties are encoded as XSD attributes:
> 
> > ### Sample Code:  
> > ```
> >    <xsd:element name="NumberToWords">
> >     <xsd:complexType abap:prefix="ZZZ_" abap:name="ZZZ_NUMBER_TO_WORDS_SOAP_REQUE" abap:description="Proxy Structure (generated)">
> >      <xsd:sequence>
> >       <xsd:element name="ubiNum" form="qualified" type="xsd:unsignedLong" abap:name="UBI_NUM" abap:type="INT8" abap:availableTypes="INT8, INT4, DEC-20"/>
> >      </xsd:sequence>
> >     </xsd:complexType>
> >    </xsd:element>
> > 
> > ```
> 
> The element `NumberToWords` being a `complexType` is represented by the dictionary structure `ZZZ_NUMBER_TO_WORDS_SOAP_REQUE` in ABAP. The element within this `complexType` `ubiNum` of XSD type `xsd:unsignedLong` corresponds to structure entry `UBI_NUM` of ABAP type `INT8`, which you could change to `INT4` or `DEC-20` \(`availableTypes`\).
> 
> The second snippet represents an exemplary `portType` section, where all ABAP properties are encoded as additional XSD elements \(prefix `wsdl`\) rather than attributes:
> 
> > ### Sample Code:  
> > ```
> > <wsdl:portType name="NumberConversionSoapType">
> >   <abap:prefix>ZZZ_</abap:prefix>
> >   <abap:name>ZZZ_CO_NUMBER_CONVERSION_SOAP</abap:name>
> >   <abap:description>Proxy Class (generated)</abap:description>
> >   <wsdl:operation name="NumberToWords">
> >    <abap:name>NUMBER_TO_WORDS</abap:name>
> >    <abap:description>Returns the word corresponding to the positive number passed</abap:description>
> >    <wsdl:input message="tns:NumberToWordsSoapRequest"/>
> >    <wsdl:output message="tns:NumberToWordsSoapResponse"/>
> >   </wsdl:operation>
> >  </wsdl:portType>
> > 
> > ```
> 
> In this code snippet, the generated ABAP class is called `ZZZ_CO_NUMBER_CONVERSION_SOAP` and its method is `NUMBER_TO_WORDS`, which corresponds to the operation `NumberToWords` of the service.

