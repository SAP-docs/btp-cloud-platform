<!-- loio3a893d98029b429da160ac133a9f7232 -->

# Enhanced Web Services Description Language \(WSDL\)

The enhanced Web Services Description Language \(WSDL\) is a WSDL enriched by ABAP information that are relevant for design time.

When you use a WSDL as an input to create a service consumption model, the information relevant for design time, such as the types, messages, and port type sections, are analyzed and interpreted by the ABAP properties. If needed, these ABAP properties can then be changed within the enhanced WSDL to adjust the ABAP artifacts accordingly \(upon re-activation\). The mapping between XSD and ABAP types in particular can be tailored this way. This results in an internal representation, where the ABAP name and type proposals are derived from. The enhanced WSDL is built from this internal representation and includes ABAP properties. That means, it is enhanced by ABAP properties. For any service consumption model, you can consider the enhanced WSDL as its service metadata.

To encode ABAP properties into the WSDL, the namespace `http://sap.com/abap/proxy` with the prefix `abap` was introduced: `xmlns:abap="http://sap.com/abap/proxy`.

For any applicable node of a WSDL, the corresponding enhanced WSDL contains additional nodes within this namespace to accommodate its ABAP properties. If there is an `abap` prefix, you can adjust the ABAP propertie. These additional nodes can be XSD attributes or elements depending on the location of the node you want to enhance. This is necessary to maintain WSDL validity. You can enhance schema nodes, such as `xmlns:xsd=http://www.w3.org/2001/XMLSchema`, via additional XSD attributes. WSDL nodes can be enhanced via additional XSD \(sub\)elements if `xmlns:wsdl=http://schemas.xmlsoap.org/wsdl/` applies. Despite the way they are encoded into the enhanced WSDL, regular ABAP properties of any node comprise the prefix, name, description. and ABAP type. With the ABAP type, you can control the mapping between XSD and ABAP types. The property `availableTypes` displays all applicable ABAP types in this case. You can chose any of the listed types by copying and pasting it into the type attribute of the given element.

<a name="loio3a893d98029b429da160ac133a9f7232__table_igc_jnw_dw"/>Summary of Additional Nodes and Their Technical Types


<table>
<tr>
<th>

Node name



</th>
<th>

Technical Type



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

abap:prefix



</td>
<td>

Up to 20 characters, case insensitive



</td>
<td>

ABAP prefix \(only used if the object is represented by an ABAP object such as `CLAS`, `INTF`, `TABL`, `DTEL`\)



</td>
</tr>
<tr>
<td>

abap:name



</td>
<td>

Up to 30 characters, case insensitive



</td>
<td>

ABAP name



</td>
</tr>
<tr>
<td>

abap:type



</td>
<td>

String, comma-separated list of 30 characters



</td>
<td>

Possible ABAP types \(only for simple types\)



</td>
</tr>
<tr>
<td>

abap:availableTypes



</td>
<td>

Maintain Business Roles



</td>
<td>

Only services whose originals reside in the current system



</td>
</tr>
<tr>
<td>

abap:description



</td>
<td>

Up to 60 characters



</td>
<td>

Description



</td>
</tr>
<tr>
<td>

abap:prefixT



</td>
<td>

See prefix



</td>
<td>

Prefix for corresponding table type \(if `maxOccurs` \> 1 and additional table type is generated and a prefix is required\)



</td>
</tr>
<tr>
<td>

abap:nameT



</td>
<td>

See name



</td>
<td>

Name for corresponding table type \(if `maxOccurs` \> 1 and additional table type is generated\)



</td>
</tr>
<tr>
<td>

abap:descriptionT



</td>
<td>

See description



</td>
<td>

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
> The element `NumberToWords` being a `complexType` is represented by the dictionary structure `ZZZ_NUMBER_TO_WORDS_SOAP_REQUE` in ABAP. The element within this `complexType` `ubiNum` of xsd type `xsd:unsignedLong` corresponds to structure entry `UBI_NUM` of ABAP type `INT8`, which you could change to `INT4` or `DEC-20` \(`availableTypes`\).
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
> In this code snippet, the generated ABAP class is called `ZZZ_CO_NUMBER_CONVERSION_SOAP` and its method is `NUMBER_TO_WORDS`, which corresponds to the operation `NumberToWord`s of the service.

